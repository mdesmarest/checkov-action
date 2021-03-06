[![Maintained by Bridgecrew.io](https://img.shields.io/badge/maintained%20by-bridgecrew.io-blueviolet)](https://bridge.dev/2WBms5Q)
[![slack-community](https://slack.bridgecrew.io/badge.svg)](https://slack.bridgecrew.io/?utm_source=github&utm_medium=organic_oss&utm_campaign=checkov-action)

# Checkov Github action

This Github Action runs [Checkov](https://github.com/bridgecrewio/checkov) against an Infrastructure-as-Code repository.
Checkov performs static security analysis of Terraform & CloudFormation Infrastructure code .


## Example usage

```yaml
jobs:
  checkov-job:
    runs-on: ubuntu-latest
    name: checkov-action
    steps:
      - name: Checkout repo
        uses: actions/checkout@master

      - name: Run Checkov action
        id: checkov
        uses: bridgecrewio/checkov-action@master
        with:
          directory: example/
          skip_check: CKV_AWS_1 # optional: skip a specific check_id
          quiet: true # optional: display only failed checks
          framework: terraform # optional: run only on a specific infrastructure {cloudformation,terraform,kubernetes,all}
```
Note that this example uses the latest version (`master`) but you could also use a static version (e.g. `v3`).
