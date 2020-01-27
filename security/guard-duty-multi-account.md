# Guard Duty Multi Account Setup

These guidelines are based on [Guard Duty Multi Account Setup](https://docs.aws.amazon.com/guardduty/latest/ug/guardduty_accounts.html)
Currently control tower does not support provisioning of Guard Duty in multiple accounts and regions.

## Setup
### Enable GuardDuty Audit Account
In order to setup guard duty in a multi-account using security account,  we need security ability for master account to launch stacksets. We will designate audit account in the multi-organization setup as guard duty master account.
- Login to audit account for organization.
- Go to GuardDuty service and enable guard duty by creating approporiate service role.
- Go to accounts and add remaining accounts in organization to this master account. Also send invitations to these accounts. [Follow step 1 and step 2 of AWS Documentation](https://docs.aws.amazon.com/guardduty/latest/ug/guardduty_accounts.html#guardduty_become_console).

### Enable StackSet Execution from Master Account
We need ability to enable guardduty for multiple accounts using our master account for organization.
- Login to AWS Organization master account and Create IAM role: AWSCloudFormationStackSetAdministrationRole using [cloudformation stack](https://s3.amazonaws.com/cloudformation-stackset-sample-templates-us-east-1/AWSCloudFormationStackSetAdministrationRole.yml)
  [One Click Deploy for us-west-2](https://console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/new?stackName=cfn-stackset-admin&templateURL=https://s3.amazonaws.com/cloudformation-stackset-sample-templates-us-east-1/AWSCloudFormationStackSetAdministrationRole.yml)
- Login to remaining accounts accounts and create IAM Role AWSCloudFormationStackSetExecutionRole using [cloudformation stack](https://s3.amazonaws.com/cloudformation-stackset-sample-templates-us-east-1/AWSCloudFormationStackSetExecutionRole.yml)
  [One Click Deploy for us-west-2](https://console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/new?stackName=cfn-stackset-execute&templateURL=https://s3.amazonaws.com/cloudformation-stackset-sample-templates-us-east-1/AWSCloudFormationStackSetExecutionRole.yml)

### Enable GuardDuty for all accounts from Master Account
Follow [these instructions](https://docs.aws.amazon.com/guardduty/latest/ug/guardduty_accounts.html#guardduty_become_stackset) to enable guardduty for all accounts in organization from master account. 
- For guardy duty master account, use audit account id.
- Since audit account is already enabled,  exclude its account id during stacket provisioning.
