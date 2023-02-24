# secrets-are-available
A composite action that checks if secrets are available on a workflow run.
Returns true if there are more secrets available than just github_token.

Use as follows:

```yaml
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v3.3.0
      - name: Find if secrets are available
        uses: DanySK/secrets-are-available@<select a valid ref here>
        with:
          secrets: ${{ toJson(secrets) }}
      - name: Runs only if there are secrets
        if: steps.test.outputs.has-secrets
        run: echo there are secrets.
```
