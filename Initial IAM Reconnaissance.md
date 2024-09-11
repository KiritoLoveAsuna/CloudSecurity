### Scoping IAM permissions
```
aws configure --profile challenge
aws --profile target sts get-caller-identity

aws --profile target iam list-user-policies --user-name clouddesk-plove
aws --profile target iam list-attached-user-policies --user-name clouddesk-plove

aws --profile target iam list-groups-for-user --user-name clouddesk-plove
aws --profile target iam list-group-policies --group-name support
aws --profile target iam list-attached-group-policies --group-name support

aws --profile target iam list-policy-versions --policy-arn "arn:aws:iam::aws:policy/job-function/SupportUser"
aws --profile target iam get-policy-version --policy-arn arn:aws:iam::aws:policy/job-function/SupportUser --version-id v8

Pacu:
ls
import_keys challenge
run iam__bruteforce_permissions
```
