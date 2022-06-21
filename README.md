# domain-protect-deploy
Deploy [Domain Protect](https://github.com/ovotech/domain-protect) using GitHub Actions

* Deploy Domain Protect in your own environment
* No need to clone or fork Domain Protect
* Internal / private deployment repository to protect your sensitive information
* Easily update to latest version of Domain Protect by running pipeline

<img src="docs/images/pipeline.png">

## how to set up
* [Create deployment IAM policy](docs/POLICY.md)
* [Create OpenID Connect IAM role](docs/OIDC.md)
* [Create and configure deployment repository](docs/OIDC.md)
* [Deploy using GitHub Actions](docs/OIDC.md)

## keeping up to date with Domain Protect
* create a custom watch on the Domain Protect repository
* when notified of a new release, run your GitHub Actions pipeline
