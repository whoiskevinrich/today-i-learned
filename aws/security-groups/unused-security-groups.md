# Unused Security Groups

Unused security groups can lead to security vulnerabilities. They can be detected and removed to improve the security posture of your AWS environment.

Unused security groups will have no network adapters associated with them. This can be checked using the AWS CLI or SDKs.

```bash
aws ec2 describe-security-groups --filters Name=group-id,Values=<security-group-id> --query 'NetworkInterfaces[].PrivateIpAddresses'
```
return `[]` if there are no network interfaces associated with the security group.