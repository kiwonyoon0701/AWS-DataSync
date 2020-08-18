# How to make VPN connection between AWS and OCI
<a href="">

# How to Create NFS in linux
<a href="">

*Check Files in NFS in OCI* 

<kbd> ![GitHub Logo](DataSync-AWS-OCI-VPN-NFS-images/16.png) </kbd>

<kbd> ![GitHub Logo](DataSync-AWS-OCI-VPN-NFS-images/17.png) </kbd>



# DataSync Manual

https://docs.aws.amazon.com/datasync/latest/userguide/create-agent-cli.html

https://docs.aws.amazon.com/datasync/latest/userguide/datasync-network.html

# Deploy DataSync Agent AMI in AWS

*https://docs.aws.amazon.com/ko_kr/datasync/latest/userguide/deploy-agents.html*

*Check Latest datasync agent AMI*
```
kiwony@kiwonymac.com:/Users/kiwony> export region=ap-northeast-1
kiwony@kiwonymac.com:/Users/kiwony> aws ssm get-parameter --name /aws/service/datasync/ami --region $region
kiwony@kiwonymac.com:/Users/kiwony> aws ssm get-parameter --name /aws/service/datasync/ami --region $region|jq
{
  "Parameter": {
    "Name": "/aws/service/datasync/ami",
    "Type": "String",
    "Value": "ami-02de0268b0efe9fc7",
    "Version": 13,
    "LastModifiedDate": "2020-07-21T00:27:24.496000+09:00",
    "ARN": "arn:aws:ssm:ap-northeast-1::parameter/aws/service/datasync/ami",
    "DataType": "text"
  }
}
```

# Launch Create DataSync Agent AMI

**Services => EC2 => Launch Instance**

*Step 1: Choose an Amazon Machine Image (AMI) : ami-02de0268b0efe9fc7*

<kbd> ![GitHub Logo](DataSync-AWS-OCI-VPN-NFS-images/1.png) </kbd>

*Step 2 : Choose Instance type*

*Step 3: Configure Instance Details*

*Step 4: Add Storage*

*Step 5: Add Tags*

*Step 6: Configure Security Group*

https://docs.aws.amazon.com/datasync/latest/userguide/datasync-network.html

*Network Requirements When Using VPC Endpoints* 

<kbd> ![GitHub Logo](DataSync-AWS-OCI-VPN-NFS-images/2.png) </kbd>

*Network Requirements When Using Public Service Endpoints or FIPS Endpoints*

<kbd> ![GitHub Logo](DataSync-AWS-OCI-VPN-NFS-images/3.png) </kbd>

<kbd> ![GitHub Logo](DataSync-AWS-OCI-VPN-NFS-images/4.png) </kbd>

*Step 7: Review Instance Launch*


# Create Agent

**Services => DataSync => Agent => "Create Agent"**

*Check IP*

<kbd> ![GitHub Logo](DataSync-AWS-OCI-VPN-NFS-images/5.png) </kbd>

*Deploy agent : Hypervisor : Amazon EC2*


<kbd> ![GitHub Logo](DataSync-AWS-OCI-VPN-NFS-images/6.png) </kbd>

<kbd> ![GitHub Logo](DataSync-AWS-OCI-VPN-NFS-images/7.png) </kbd>

*Create Aent Click*

<kbd> ![GitHub Logo](DataSync-AWS-OCI-VPN-NFS-images/8.png) </kbd>


# Create Location - Source

**DataSync => Location => "Craete Location"

```
Location Type : NFS
Agents : agent 
NFS Server : 10.0.0.3(OCI NFS)
Mount Path : /nfs (OCI NFS)
```

<kbd> ![GitHub Logo](DataSync-AWS-OCI-VPN-NFS-images/9.png) </kbd>

*Create Location Click* 

# Create Location - Target

**DataSync => Location => "Craete Location"

```
Location Type : Amazon S3 bucket
S3 Bucket : S3 bucket
S3 Storage Class : Standard
IAM role : Autogenerate
```

<kbd> ![GitHub Logo](DataSync-AWS-OCI-VPN-NFS-images/10.png) </kbd>

*Create Location Click* 

# Check 2 locations

<kbd> ![GitHub Logo](DataSync-AWS-OCI-VPN-NFS-images/11.png) </kbd>

# Create Tasks

**DataSync => Tasks => "Craete task"

<kbd> ![GitHub Logo](DataSync-AWS-OCI-VPN-NFS-images/12.png) </kbd>

<kbd> ![GitHub Logo](DataSync-AWS-OCI-VPN-NFS-images/13.png) </kbd>

<kbd> ![GitHub Logo](DataSync-AWS-OCI-VPN-NFS-images/14.png) </kbd>

<kbd> ![GitHub Logo](DataSync-AWS-OCI-VPN-NFS-images/15.png) </kbd>

*Wating for Task status is Available*

<kbd> ![GitHub Logo](DataSync-AWS-OCI-VPN-NFS-images/18.png) </kbd>

*Check S3 bucket*

<kbd> ![GitHub Logo](DataSync-AWS-OCI-VPN-NFS-images/19.png) </kbd>

*Start DataSync Task*

<kbd> ![GitHub Logo](DataSync-AWS-OCI-VPN-NFS-images/20.png) </kbd>

<kbd> ![GitHub Logo](DataSync-AWS-OCI-VPN-NFS-images/21.png) </kbd>


*Waiting for task completion*

<kbd> ![GitHub Logo](DataSync-AWS-OCI-VPN-NFS-images/22.png) </kbd>

<kbd> ![GitHub Logo](DataSync-AWS-OCI-VPN-NFS-images/23.png) </kbd>

<kbd> ![GitHub Logo](DataSync-AWS-OCI-VPN-NFS-images/24.png) </kbd>

<kbd> ![GitHub Logo](DataSync-AWS-OCI-VPN-NFS-images/25.png) </kbd>




