# Guard Duty Multi Account Setup

These guidelines are based on [Guard Duty Multi Account Setup](https://docs.aws.amazon.com/guardduty/latest/ug/guardduty_accounts.html)

## Setup
### Stack Set Setup
In order to setup guard duty in a multi-account using security account,  we need security ability for master account to launch stacksets.
- Login to master for organization.
- Create IAM role: AWSCloudFormationStackSetAdministrationRole using [cloudformation stack](https://s3.amazonaws.com/cloudformation-stackset-sample-templates-us-east-1/AWSCloudFormationStackSetAdministrationRole.yml)
  [One Click Deploy for us-west-2](https://console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/new?stackName=cfn-stackset-admin&templateURL=https://s3.amazonaws.com/cloudformation-stackset-sample-templates-us-east-1/AWSCloudFormationStackSetAdministrationRole.yml)
