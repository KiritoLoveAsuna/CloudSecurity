### Get policy details
```
aws --profile target iam list-attached-user-policies --user-name clouddesk-plove
aws --profile target iam list-policy-versions --policy-arn arn:aws:iam::12345678912:policy/deny_challenges_access

aws --profile target iam get-account-authorization-details --filter LocalManagedPolicy
```
### Gain Account Info
```
aws --profile target iam get-account-summary | tee account-summary.json
aws --profile target iam list-users | tee  users.json
aws --profile target iam list-groups | tee groups.json
aws --profile target iam list-roles | tee roles.json
```
### Find Privilege Escalation Vector
```
List all user info:
aws --profile target iam get-account-authorization-details --filter User

List One Group info:
aws --profile target iam get-account-authorization-details --filter Group --query "GroupDetailList[?GroupName=='admin']"

List one user info:
aws --profile target iam get-account-authorization-details --filter User Group --query "UserDetailList[?UserName=='admin-alice']"

List one policy info:
aws --profile target iam get-account-authorization-details --filter LocalManagedPolicy --query "Policies[?PolicyName=='amethyst_admin']"
or 
aws --profile target iam get-account-authorization-details --filter AWSManagedPolicy --query "Policies[?PolicyName=='AdministratorAccess']"
```
