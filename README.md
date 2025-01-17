## Udacity project | Deploy a high-availability web app using CloudFormation

This repository contains my solution to the Udacity project of module 2 of the course Cloud dev ops Engineer. It involves creating AWS resources such as:

1. networking infrastructure : THese include VPCs, subnets Elastic IPs, gateways, RouteTable etc
2. Servers and Server groups: THese include Secucrity groups, Autoscaling groups, launch configurations, Target groups, Listeners, Loadbalances etc.
3. Other resources: These include IAM roles, S3 buckets

### Requirements

##### 1. Creating SSH key pairs in AWS account.

You would require to create ssh keys in the aws account that will be used to access the EC2 instances that are created in both the private and public subnets. The ssh keys should be named udagram.pem and udagram-bastion.pem

##### 2. Copy the Key pairs to the specified bucket.

After creating and downloading the key pairs. You will have to add them the the S3 bucket **udagramkeypairs**. Feel free to change the name of bucket and keys if you wish. The keys are attached to EC2 instances on creation and also used in the bastion host to connect to the instances that are in private subnets.

### How to run the cloud formation scripts in this project?

You can run the scripts in two easy steps:

```bash
# Ensure that the AWS CLI is configured before runniing the command below
# Create the network infrastructure
# Check the region in the create.sh file
./create.sh network udagram-network.yml parameters/udagram-network.json
# Create servers
# Change the AMI ID and key-pair name in the servers.yml
# Check the region in the update.sh file
./update.sh server servers.yml server-parameters.json
```

### Order of execution of the scripts?

1. udagram-network.yml (./create.sh network udagram-iam.yml parameters/udagram-iam.json )
2. udagram-iam.yml (./create.sh IAMRole udagram-iam.yml parameters/udagram-iam.json)
3. udagram-s3.yml (./create.sh S3bucket udagram-s3.yml parameters/udagram-s3.json )
4. udagram-bastion.yml (./create.sh bastion udagram-bastion.yml parameters/udagram-bastion.json)
5. udagram.yml (./create.sh udagramApp udagram.yml parameters/udagram.json)

### Website link:

```bash
http://udagram-1105007005.us-west-2.elb.amazonaws.com
```
