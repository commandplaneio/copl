
# Bring your Own Cloud (BYOC) Configuration
Currently, Copl uses Github Actions runners to manage the  remote AWS accounts. It keeps the dev environments in a desired state and blocks any configuration drift.
Below is the configuration for an AWS environment.
## AWS
1. Run the command below to create the identity federation betweeen Copl Github Actions runners and your AWS estate.

```
aws iam create-open-id-connect-provider \
    --url https://token.actions.githubusercontent.com \
    --client-id-list sts.amazonaws.com 
```

2. Create the IAM role. The minimum privileges are listed [here](iam-policy.json)
3. Create a trust policy shown below for the role.
```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": {
                "Federated": "arn:aws:iam::${Account}:oidc-provider/token.actions.githubusercontent.com"
            },
            "Action": "sts:AssumeRoleWithWebIdentity",
            "Condition": {
                "StringEquals": {
                    "token.actions.githubusercontent.com:aud": "sts.amazonaws.com"
                },
                "StringLike": {
                    "token.actions.githubusercontent.com:sub": "repo:commandplaneio/IaC:*"
                }
            }
        }
    ]
}
```


## GCP
## Azure
