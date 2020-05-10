# AWS Networking Examples

Create an SSH key for your EC2 instances (e.g. my-ssh-key). Make sure to import the key to all the different regions if you want to create the stack in multiple regions.

Create CloudFormation stack in US East 1 region:
```
aws cloudformation create-stack --region us-east-1 --stack-name NetworkingDemo --template-body file:///<path-to-project>/templates/vpc-1.yaml --parameters ParameterKey=VPCCidrBlock,ParameterValue='10.1.0.0/16' ParameterKey=KeyName,ParameterValue=my-ssh-key ParameterKey=ImageId,ParameterValue=ami-0323c3dd2da7fb37d
```

Create CloudFormation stack in US West 1 region:
```
aws cloudformation create-stack --region us-west-1 --stack-name NetworkingDemo --template-body file:///<path-to-project>/templates/vpc-1.yaml --parameters ParameterKey=VPCCidrBlock,ParameterValue='10.2.0.0/16' ParameterKey=KeyName,ParameterValue=my-ssh-key ParameterKey=ImageId,ParameterValue=ami-06fcc1f0bc2c8943f
```

Delete CloudFormation stacks:
```
aws cloudformation delete-stack --region <region-name> --stack-name NetworkingDemo
```

## Network Topology

## Connecting to Private Servers

https://aws.amazon.com/blogs/security/securely-connect-to-linux-instances-running-in-a-private-amazon-vpc/
