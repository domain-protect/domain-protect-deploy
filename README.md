# domain-protect-deploy
Deploy [Domain Protect](https://github.com/domain-protect/domain-protect) using GitHub Actions

* Deploy Domain Protect in your AWS environment
* No need to clone or fork Domain Protect
* Internal / private deployment repository to protect sensitive information
* Uses OpenID Connect - no IAM user with long-lived access keys
* Update to latest version of Domain Protect any time by running pipeline

<img src="docs/images/pipeline.png">

## pipeline steps
Pipeline triggered manually and also on `git push` of the main branch

* Terraform plan and apply of Domain Protect dev in security tooling account 
* Terraform plan for Domain protect prd in security tooling account (approval required)
* Terraform apply for Domain protect prd in security tooling account (approval required)

Both dev and prd are deployed to the production security tooling account, as this will have rights to assume the audit role in all AWS accounts in the Organization.

## before starting
* check [requirements](https://github.com/domain-protect/domain-protect/blob/main/docs/requirements.md)

## how to set up
* [Create deployment IAM policy](docs/POLICY.md)
* [Create OpenID Connect IAM role](docs/OIDC.md)
* [Create and configure deployment repository](docs/REPO.md)
* [Deploy using GitHub Actions](docs/DEPLOY.md)

## keep up to date with Domain Protect
* create a custom watch on Domain Protect repository
* when notified of a new release, run your GitHub Actions pipeline
