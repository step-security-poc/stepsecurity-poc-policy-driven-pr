# Policy Driven PR's – Automating Fixes with Pull Requests 
 
Policy Driven PR's allow you to automate security remediation across your repositories by automatically generating Pull Requests to fix issues or creating GitHub Issues to track vulnerabilities. For more information, see [here](https://docs.stepsecurity.io/orchestrate-security/policy-driven-prs) 

## Supported Controls
This feature allows you to automatically fix and align with the following controls:

* **Harden GitHub-Hosted Runner**: Ensures Harden-Runner is installed on GitHub-hosted runners. Often used to deploy harden-runner at scale
* **Pin Actions to Full-Length Commit SHA**: Pin actions to full-length commit SHAs to follow best security practices
* **Restrict GitHub Token Permissions**: Restrict default GitHub token permissions to minimal required permissions 
* **Pin image tags to digests in Dockerfiles**: Docker tags are mutable, so use digests in place of tags when pulling images
* **Replace third party actions with StepSecurity maintained actions**: Use secure, audited GitHub actions maintained by StepSecurity to reduce supply chain risks
* **Update Dependabot configuration**: Manage Dependabot configuration to help keep dependency versions up to date 
* **Update the pre-commit configuration**: Pre-commit hooks are useful for enforcing code quality, code formatting, and detecting security vulnerabilities.
* **Add GitHub Actions from the Workflows Templates**: Add workflows that are part of the organization's recommended set and were previously missing from the repository

## Testing Controls 

Policy Driven PR's can be applied on a repo by repo basis or across your entire organization. It can be enabled from the StepSecurity dashboard under `Orchestrate Security -> Policy Driven PR's`. Once enabled, daily scans will check for misconfigurations based on the selected controls and automatically create a pull request if any are found

To test this feature, the quickest way to get started is to use an existing repository within your organization, or create a test repository. This repository contains workflows and configurations that will fail the controls above (ie; replacing action with maintained action, adding dependabot configuration) - prompting a PR to be opened to fix the issues. 

* You can use the [workflow file](https://github.com/stepsecurity-poc/stepsecurity-poc-policy-driven-pr/blob/main/.github/workflows/misconfigured.yml) in your own repository for testing. It may take up to 1 hour for the actions to reflect in the StepSecurity dashboard
* Enable Policy Driven PR's from the StepSecurity dashboard under the `Policy Driven PR's` section
  1)  Select which controls you want to apply for the policy
  2) Select which repositories you want the policy to apply to (for testing purposes, you can select just your test repository)
  3) Once you enable `Replace third-party actions with StepSecurity maintained actions`, you will be prompted to select which actions to replace. Select any available maintained actions. If none are showing, you may need to wait up to 1 hour from when you copied/ran the workflow
* Once you save the policy, it will do a scan within ~15 minutes, and open a PR to apply fixes based on the controls you selected. From here, it will do a daily scan to address misconfigurations. 

