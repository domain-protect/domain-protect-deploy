## Create repo in your own GitHub Organisation
* create a private or internal repository `domain-protect-deploy` in your organisation
```
git clone https://github.com/domain-protect/domain-protect-deploy
git remote rename origin upstream
git remote add origin https://YOUR_GITHUB_ORG/domain-protect-deploy
git push origin main
```

## Set up GitHub Actions environment
* a GitHub Actions environment is needed for manual approval steps
* within the GitHub repository web console, select Settings, Code and automation, Environments
* create a new environment `prd`
<img src="images/actions-environment.png" width="500">
* configure Environment protect rules
* select Required reviewers
* enter an appropriate team
<img src="images/actions-env-protection.png" width="500">
* save protection rules

## Enter secrets
* at Settings, Security, Secrets, Actions, enter Repository secrets:

| REPOSITORY SECRETS              | EXAMPLE VALUE / COMMENT                          |
| ------------------------------- | -------------------------------------------------|
| AWS_DEPLOY_ROLE_ARN             | arn:aws:iam::123456789012:role/domain-protect-oidc-github |
| AWS_REGION                      | eu-west-1    |
| TERRAFORM_STATE_BUCKET          | tfstate48903                                     |
| TERRAFORM_STATE_KEY             | domain-protect                                   |
| TERRAFORM_STATE_REGION          | us-east-1                                        |  
| ORG_PRIMARY_ACCOUNT             | 012345678901                                     | 
| SECURITY_AUDIT_ROLE_NAME        | not needed if "domain-protect-audit" used        |
| EXTERNAL_ID                     | only required if External ID is configured       |
| SLACK_CHANNELS                  | ["security-alerts"]                              |
| SLACK_CHANNELS_DEV              | ["security-alerts-dev"]                          |
| SLACK_WEBHOOK_URLS              | ["https://hooks.slack.com/services/XXX/XXX/XXX"] | 

<img src="images/actions-secrets.png" width="500">

Environment variables should be created as secrets where:
* the information is sensitive, e.g. an API key
* the variable would otherwise require double quotes, e.g. a list with string elements

## Update deploy.yml
* remove unwanted environment variables, for example if you're not using any optional features, and you want the standard DynamoDB database sizing, delete these lines in the initial the `env` block at the start of [workflow](../.github/workflows/deploy.yml)
```
  TF_VAR_cloudflare: true
  TF_VAR_cf_api_key: ${{ secrets.CF_API_KEY }}
  TF_VAR_rcu: 1
  TF_VAR_wcu: 1
  TF_VAR_ip_address: true
  TF_VAR_allowed_regions: ${{ secrets.ALLOWED_REGIONS }}
```
* enter additional environment variables to turn on optional features
* enter additional environment variables to customise settings
* ensure each secret has a corresponding definition in the `env` block at the start of [workflow](../.github/workflows/deploy.yml)
```
git commit -am "environment variable update"
git push
```