### Get policy details
```
aws --profile target iam list-attached-user-policies --user-name clouddesk-plove
aws --profile target iam list-policy-versions --policy-arn arn:aws:iam::12345678912:policy/deny_challenges_access

aws --profile target iam get-account-authorization-details --filter LocalManagedPolicy
```
