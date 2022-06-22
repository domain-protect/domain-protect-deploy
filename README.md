# domain-protect-deploy
Deploy [Domain Protect](https://github.com/ovotech/domain-protect) using GitHub Actions

* Deploy Domain Protect in your AWS environment
* No need to clone or fork Domain Protect
* Internal / private deployment repository to protect sensitive information
* Uses OpenID Connect - no IAM user with long-lived access keys
* Update to latest version of Domain Protect any time by running pipeline

<img src="docs/images/pipeline.png">

## before starting
* check prerequisites detailed in main [Domain Protect](https://github.com/ovotech/domain-protect) documentation

## how to set up
* [Create deployment IAM policy](docs/POLICY.md)
* [Create OpenID Connect IAM role](docs/OIDC.md)
* [Create and configure deployment repository](docs/REPO.md)
* [Deploy using GitHub Actions](docs/DEPLOY.md)

## keeping up to date with Domain Protect
* create a custom watch on Domain Protect repository
* when notified of a new release, run your GitHub Actions pipeline
