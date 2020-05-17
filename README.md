# AWS Networking Examples

Create an SSH key for your EC2 instances (e.g. my-ssh-key). Make sure to import the key to all the different regions if you want to create the stack in multiple regions.

Create CloudFormation stack in US East 1 region:
```
aws cloudformation create-stack --region us-east-1 --stack-name NetworkingDemo --template-body file:///`pwd`/templates/vpc-1.yaml --parameters ParameterKey=KeyName,ParameterValue=my-ssh-key
```

Create CloudFormation stack in US West 1 region:
```
aws cloudformation create-stack --region us-west-1 --stack-name NetworkingDemo --template-body file:///`pwd`/templates/vpc-1.yaml --parameters ParameterKey=KeyName,ParameterValue=my-ssh-key
```

The CloudFormation stack contains a mapping that link US regions to non-overlaping CIDRs and EC2 image IDs.

Delete CloudFormation stacks:
```
aws cloudformation delete-stack --region <region-name> --stack-name NetworkingDemo
```

## Connecting to Private Servers

Private instances are only reachable through the bastion hosts.

First, SSH into one of the bastion host with forwarding enable:

```
ssh -A ec2-user@<bastion host public IP or DNS>
```

Then, SSH into the private instance:

```
ssh ec2-user@<private instance IP or DNS>
```

You can find more information in this [AWS article](https://aws.amazon.com/blogs/security/securely-connect-to-linux-instances-running-in-a-private-amazon-vpc/)
