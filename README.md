<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# VPC Endpoints

**Project Link:** [View Project](http://nextwork.ai/projects/aws-networks-endpoints)

**Author:** irahimsindhu@gmail.com  
**Email:** irahimsindhu@gmail.com

---

## VPC Endpoints

![Image](http://nextwork.ai/affectionate_olive_majestic_marjoram/uploads/aws-networks-endpoints_09bcaa8a)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC is a virtual private network in AWS, and it is useful because it lets you securely control your cloud resources, networking, and access settings.

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC to securely connect to my S3 bucket through a VPC endpoint and control access using policies.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was the clear guidance and the simplicity in explanation.

### This project took me...

This project took me 55 minutes to complete.

---

## In the first part of my project...

### Step 1 - Architecture set up

In this step, I will set up the following:
- VPC,
- EC2 instance,
- S3 Bucket

### Step 2 - Connect to EC2 instance

In this step, I will be connected directly to my EC2 instance using AWS Connect.

### Step 3 - Set up access keys

In this step, I will give my EC2 instance access to your AWS environment.

### Step 4 - Interact with S3 bucket

In this step, I will demonstrate the following:
- Head back to your EC2 instance.
- Get your EC2 instance to access your S3 bucket.

---

## Architecture set up

I started my project by launching a VPC and an EC2 instance inside the VPC.

I also set up a S3 bucket and uploaded 2 files from my laptop in the bucket.

![Image](http://nextwork.ai/affectionate_olive_majestic_marjoram/uploads/aws-networks-endpoints_4334d777)

---

## Access keys

### Credentials

To set up my EC2 instance to interact with my AWS environment, I configured my AWS access keys, my default region and default output format.

Access keys are credentials for your applications and other servers to log into AWS and talk to your AWS services/resources.

Secret access keys are like the password that pairs with your access key ID (your username). You need both to access AWS services.

Secret is a key word here - anyone who has it can access your AWS account, so we need to keep this away from anyone else!

### Best practice

Although I'm using access keys in this project, a best practice alternative is to use IAM roles with temporary credentials.

---

## Connecting to my S3 bucket

The command I ran was "aws s3 ls".This command is used to list down all the S3 buckets in my AWS account.

The terminal responded with:
2026-06-16 21:22:33 nextwork-vpc-project-rahim
2026-06-23 21:00:47 nextwork-vpc-project-rahim1
This indicated that the access keys I set up are configured correctly.

![Image](http://nextwork.ai/affectionate_olive_majestic_marjoram/uploads/aws-networks-endpoints_4334d778)

---

## Connecting to my S3 bucket

I also tested the command 
"aws s3 ls s3://nextwork-vpc-project-rahim1"
 which returned all the contents of my S3 bucket.

![Image](http://nextwork.ai/affectionate_olive_majestic_marjoram/uploads/aws-networks-endpoints_4334d779)

---

## Uploading objects to S3

To upload a new file to my bucket, I first ran the command:
"sudo touch /tmp/nextwork.txt"
This command creates a temporary file in my AWS console

The second command I ran was:
"aws s3 cp /tmp/nextwork.txt s3://nextwork-vpc-project-rahim1"
This command will copy the temporary file in the specific S3 bucket.

The third command I ran was:
"aws s3 ls s3://nextwork-vpc-project-rahim1"
which validated that the file has been added the S3 bucket by displaying the contents of the bucket.

![Image](http://nextwork.ai/affectionate_olive_majestic_marjoram/uploads/aws-networks-endpoints_3e1e79a2)

---

## In the second part of my project...

### Step 5 - Set up a Gateway

In this step, I will demostrate:
- Set up a way for your VPC and S3 to communicate direclty.

### Step 6 - Bucket policies

In this step, I'm limiting the access to my S3 bucket to only traffic allowed from my endpoint.

### Step 7 - Update route tables

In this step, I will:
- Test your VPC endpoint set up.
- Troubleshoot a connectivity issue.

### Step 8 - Validate endpoint conection

In this step, I will demonstrate the following:
- Test your VPC endpoint set up (again).
- Restrict your VPC's acccess to your AWS environment.



---

## Setting up a Gateway

I set up an S3 Gateway, which is a type of endpoint used specifically for Amazon S3 and DynamoDB (DynamoDB is an AWS database service).

Gateways work by simply adding a route to your VPC route table that directs traffic bound for S3 or DynamoDB to head straight for the Gateway instead of the internet.



### What are endpoints?

An endpoint is a service that allows private connections between your VPC and other AWS services without needing the traffic to go over the internet.

![Image](http://nextwork.ai/affectionate_olive_majestic_marjoram/uploads/aws-networks-endpoints_09bcaa8a)

---

## Bucket policies

A bucket policy is a resource-based policy that controls access to an S3 bucket and its objects.

My bucket policy will deny access to the S3 bucket unless requests come through the specified VPC endpoint.


![Image](http://nextwork.ai/affectionate_olive_majestic_marjoram/uploads/aws-networks-endpoints_7316a13d)

---

## Bucket policies

Right after saving my bucket policy, my S3 bucket page showed 'denied access' warnings. This was because the access to S3 was denied from everywhere else including IAM Management Console.

I also had to update my route table because if my route table doesn't have a route that directs traffic bound for S3 to your VPC endpoint, traffic from your EC2 instance is actually trying to get to your S3 bucket through the public internet instead.


![Image](http://nextwork.ai/affectionate_olive_majestic_marjoram/uploads/aws-networks-endpoints_4ec7821f)

---

## Route table updates

To update my route table, I added the route table in my VPC endpoint's route table setting.

After updating my public subnet's route table, my terminal could return all the contents of my S3 bucket.

![Image](http://nextwork.ai/affectionate_olive_majestic_marjoram/uploads/aws-networks-endpoints_d116818e)

---

## Endpoint policies

An endpoint policy is a resource-based policy that controls which AWS resources can be accessed through a VPC endpoint.

I updated my endpoint's policy by:
"Effect": "Deny"
I could see the effect of this right away, because all requests through the VPC endpoint were immediately denied by the endpoint policy.

![Image](http://nextwork.ai/affectionate_olive_majestic_marjoram/uploads/aws-networks-endpoints_3e1e79a3)

---

---
