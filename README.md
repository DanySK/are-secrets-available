# are-secrets-available
A composite action that checks if secrets are available on a workflow run.
Returns true if there are more secrets available than just github_token.

## Usage

Use as follows:

```yaml
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v3.3.0
      - name: Find if secrets are available
        id: secrets
        uses: DanySK/are-secrets-available@<select a valid ref here>
        with:
          secrets: ${{ toJson(secrets) }}
      - name: Runs only if there are secrets
        if: steps.secrets.outputs.has-secrets
        run: echo there are secrets.
```
