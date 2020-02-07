# Organization Guardrails
Most of the guard rails are automatically setup by Controltower. This document defines additional guardails and protection that
we recommend to enable for every organizations

## Restrict Unused Regions
In order to prevent someone from accidentally creating resources in a region which is not used by the organization,  we should
restrict it using service control policies. For a multi-organization setup, add following policy and apply it to Root organization unit. 

For instance, if we want to restrict the usage to us-west-2 region for region specific services,  create following service control policy: 

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "DenyUnusedRegions",
            "Effect": "Deny",
            "NotAction": [
                "iam:*",
                "organizations:*",
                "route53:*",
                "budgets:*",
                "waf:*",
                "cloudfront:*",
                "globalaccelerator:*",
                "importexport:*",
                "support:*",
                "trustedadvisor:*"
            ],
            "Resource": "*",
            "Condition": {
                "StringNotEquals": {
                    "aws:RequestedRegion": [
                        "us-west-2"
                    ]
                }
            }
        }
    ]
}
```
