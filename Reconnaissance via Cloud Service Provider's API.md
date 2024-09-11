### Describe VPCs with assumed role 
```
aws configure --profile attacker
pacu
impport_keys attacker
set_keys <access_key> <secret_key> <session_token>
aws ec2 describe-vpcs --region us-east-1
```
### Obtain id
```
aws sts get-caller-identity --profile enum
```
