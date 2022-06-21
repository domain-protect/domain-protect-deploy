# Deploy
* In `YOUR_GITHUB_ORG/domain-protect-deploy` select Actions
* Workflow triggers automatically on `git push`
* To trigger manually, select the Deploy Domain Protect workflow
<img src="images/manual-trigger.png" width="500">
* Press Run workflow
* Choose the main branch
<img src="images/workflow-needs-approval.png" width="500">
* When prompted, press Review deployments
<img src="images/workflow-approval.png" width="300"> 
* Approve to proceed to production
* Review Terraform plan and approve again to apply in production
<img src="images/pipeline.png">
* Terraform plan is available as an artifact for download
