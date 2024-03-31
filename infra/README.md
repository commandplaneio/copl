
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
2. The minimum privileges are listed [here](iam-policy.json)
3. Create the IAM role. Assign the permissions/policy created above.
4. Create a trust policy defined [here](trust-policy.json)

## GCP
## Azure
