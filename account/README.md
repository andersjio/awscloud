### Create AWS Profile

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "VisualEditor0",
            "Effect": "Allow",
            "Action": [
                "organizations:DeclineHandshake",
                "organizations:ListTargetsForPolicy",
                "organizations:ListTagsForResource",
                "organizations:DetachPolicy",
                "organizations:DeletePolicy",
                "organizations:UntagResource",
                "organizations:AcceptHandshake",
                "organizations:DescribePolicy",
                "organizations:CancelHandshake",
                "organizations:TagResource",
                "organizations:UpdatePolicy",
                "organizations:AttachPolicy",
                "organizations:DescribeHandshake"
            ],
            "Resource": [
                "arn:aws:organizations::*:handshake/o-*/*/h-*",
                "arn:aws:organizations::*:policy/o-*/*/p-*"
            ]
        },
        {
            "Sid": "VisualEditor1",
            "Effect": "Allow",
            "Action": [
                "organizations:ListRoots",
                "organizations:DisableAWSServiceAccess",
                "organizations:CreateAccount",
                "organizations:DeleteOrganization",
                "organizations:ListAWSServiceAccessForOrganization",
                "organizations:ListPolicies",
                "organizations:ListHandshakesForOrganization",
                "organizations:ListDelegatedAdministrators",
                "organizations:LeaveOrganization",
                "organizations:ListHandshakesForAccount",
                "organizations:ListAccounts",
                "organizations:EnableAWSServiceAccess",
                "organizations:ListCreateAccountStatus",
                "organizations:DescribeOrganization",
                "organizations:CreateGovCloudAccount",
                "organizations:EnableAllFeatures",
                "organizations:CreatePolicy",
                "organizations:DescribeCreateAccountStatus",
                "organizations:CreateOrganization"
            ],
            "Resource": "*"
        }
    ]
}
```

### Create account

Create an AWS account
AWS_PROFILE=createAccount

```bash
aws organizations --profile <AWS_PROFILE> create-account \
    --email <EMAIL> \
    --account-name <ACCOUNT NAME>
```

### Get status for Account creation

```bash
aws organizations list-create-account-status --states IN_PROGRESS --profile <AWS_PROFILE>
```
Should return empty list when account(s) have been created


### Move Account to OU

```bash
aws organizations move-account --account-id <ACCOUNT_ID> --source-parent-id <ROOT_ACCOUNT_ID> --destination-parent-id <DESTINATION_ACCOUNT_ID> --profile <AWS_PROFILE>
```

### Close AWS account

```bash
aws organizations close-account --account-id <ACCOUNT_ID> --profile <AWS_PROFILE>
```