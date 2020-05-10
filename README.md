# AWS Networking Examples

Create an SSH key for your EC2 instances (e.g. my-ssh-key).

Create CloudFormation stack:
```
aws cloudformation create-stack --stack-name NetworkingTest --template-body file:///<path-to-project>/templates/vpc-1.yaml --parameters ParameterKey=KeyName,ParameterValue=my-ssh-key ParameterKey=ImageId,ParameterValue=ami-0323c3dd2da7fb37d
```

Delete CloudFormation stack:
```
aws cloudformation delete-stack --stack-name NetworkingTest
```
