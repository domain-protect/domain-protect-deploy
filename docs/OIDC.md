## OpenID Connect configuration in AWS
* log in to your security tooling AWS account and go to IAM
* select Identity providers
<img src="images/oidc-provider-details.png" width="500">
* add an Identity Provider
* choose OpenID Connect
* for the Provider URL enter `token.actions.githubusercontent.com`
* press Get thumbprint
* for Audience enter sts.amazonaws.com
* press Add Provider
<img src="images/oidc-provider-created.png" width="500">
* select the newly added Identity Provider
* press Assign Role
<img src="images/create-new-role.png" width="400">
* select Create a new role
* press Next
<img src="images/create-role-wizard-1.png" width="500">
* for Audience, choose `sts.amazonaws.com` from the drop-down
* press Next: Permissions
<img src="images/create-role-wizard-2.png" width="500">
* select `domain-protect-deploy` policy
* press Next: Tags
* press Next: Review
<img src="images/create-role-wizard-3.png" width="500">
* name the new role `domain-protect-oidc-github`
* enter an appropriate description
* press Create role
* edit the Trust Policy - THIS MUST BE DONE IMMEDIATELY - OTHERWISE ANYONE IN THE WORLD CAN ASSUME THE ROLE
<img src="images/update-trust-policy.png" width="500">
* enter the second statement under `StringEquals`:
```
"Condition": {
                "StringEquals": {
                    "token.actions.githubusercontent.com:aud": "sts.amazonaws.com",
                    "token.actions.githubusercontent.com:sub": [
                        "repo:YOUR_GITHUB_ORG/domain-protect-deploy:ref:refs/heads/main"
                    ]
                }
            }
```