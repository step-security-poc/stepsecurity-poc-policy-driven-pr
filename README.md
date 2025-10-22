# Policy Driven PR's – Automating Fixes with Pull Requests 
 
Policy Driven PR's allow you to automate security remediation across your repositories by either automatically generating Pull Requests to fix issues or creating GitHub Issues to track vulnerabilities. For more information, see [here](https://docs.stepsecurity.io/orchestrate-security/policy-driven-prs) 

## How it works

Policy Driven PR's allow you to define specific controls and best practices to automate via pull requests. This can be enabled from the StepSecurity dashboard under `Orchestrate Security -> Policy Driven PR's`. The policy can be applied to individually to repositories, or all repositories. 

For the purpose of testing this in a POC, you can choose to turn this on for your own internal repositories, or use this repository as a reference

## Testing Controls 

* This Repository contains a workflow with low scoring actions. You can copy the workflow file in your own repository for testing. It may take up to 1 hour for the actions to reflect in the StepSecurity dashboard
* Enable Policy Driven PR's from the StepSecurity dashboard under the `Policy Driven PR's` section
  1)  Select which controls you want to apply for the policy
  2) Select which repositories you want the policy to apply to (for testing purposes, you can select just your test repository)
  3) Once you enable `Replace third-party actions with StepSecurity maintained actions`, you will be prompted to select which actions to replace. Select any available maintained actions. If none are showing, you may need to wait up to 1 hour from when you copied/ran the workflow
* Once you save the policy, it will do a scan within ~15 minutes, and open a PR to apply fixes based on the controls you selected. From here, it will do a daily scan to address misconfigurations. 

