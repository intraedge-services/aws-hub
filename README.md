# aws-hub
AWS Professional Services Hub

## About
This is a central hub for Intraedge Professional Services best practices around AWS. AS AWS evolves and launches new services, we constantly update our practices in order to lower the cost for our customers.
These practices will be versioned in our github repositories to provide support to our customers who started with a particular version. 
These practices are designed considering five pillars of [AWS Well Architected Framework](https://aws.amazon.com/architecture/well-architected/). We have decided to open source these practices for any organizations to adopt the same or provide suggestions 

## Account Setup
Our core strategy for AWS accounts uses following guidelines and highly:

- Separate AWS accounts for different environments. (Dev, QA, Production)
- Separate AWS accounts for different teams managing particular business function in an organization. 
- A master AWS account to manage billing, organization level guardrails for all the sub accounts.
- A separate logging AWS account to centralize audit trail across all accounts.
- A separate security AWS account to manage security control for all AWS accounts.
- [AWS Organizations](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_introduction.html) to manage organizations hierarchy.
- [AWS SSO](https://docs.aws.amazon.com/singlesignon/latest/userguide/what-is.html) for single sign on across separate accounts.
- [AWS Service Control Policies](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scp.html) to create guardrails for all the accounts in the organization.

### New Accounts
As our best strategy for our new customers on AWS, we recommend our customers to start with a multi-account setup strategy. With the launch of [AWS Control Tower](https://docs.aws.amazon.com/controltower/latest/userguide/what-is-control-tower.html) , we have adopted our practices to support the same.

### Existing Accounts
FOr existing accounts, we highly recommend to migrate to a multi-account setup usung [AWS Organizations](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_introduction.html) and set organization-wide guard rails.


## Support
For commercial support and professional services contact cloudsales@intraedge.com
