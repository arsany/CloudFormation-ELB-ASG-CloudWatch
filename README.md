CloudFormation Project 

*For the diagram you can check CloudFormation.pdf*

Here is HA-Application using ELB-ASG and Cloud watch 

using Create.sh bash file you can spacify stack-name , template-body and parameters

First you need to build the VPC using CloudFormation-VPC.yaml with it's json parameters using this command 

       aws cloudformation create-stack --stack-name Example --template-body file://CloudFormation-VPC.yaml \
       --parameters file://params-CloudFormation-VPC.json  

Then you will build the ELB-ASG-cloudwatch and publish the web-app using 
CloudFormation-ELB-ASG-CW.yaml with it's json parameters.

        aws cloudformation create-stack --stack-name Example --template-body file://CloudFormation-ELB-ASG-CW.yaml \
        --parameters file://params-CloudFormation-ELB-ASG-CW.json  --capabilities CAPABILITY_NAMED_IAM


Finaly you will get output with DNSname from ELB to access the Application. 


REQUIREMENTS
•VPC with private/public subnets and all required dependent infrastructure (DO NOT USE THEDEFAULT VPC)
•ELB to be used to register web server instances
oInclude a simple health check to make sure the web servers are responding
oThe health check should automatically replace instances if they are unhealthy, and theinstances should come back into service on their own
•Auto Scaling Group and Launch Configuration that launches EC2 instances and registers themto the ELB
oEstablish a minimum, maximum, and desired server count that scales up/down based ona metric of your choice (and be able to demonstrate a scaling event)
•Security Group allowing HTTP traffic to load balancer from anywhere (not directly to theinstance(s))
•Security Group allowing only HTTP traffic from the load balancer to the instance(s)
•Remote management ports such as SSH and RDP must not be open to the world
•Some kind of automation or scripting that achieves the following:
  Install a web server (your choice – Apache and Nginx are common examples)
  Deploys a simple “hello world” page for the web server to serve up
  Can be written in the language of your choice (HTML, PHP, etc)
  Can be sourced from the location of your choice (S3, cookbook file/ template, etc)
  Must include the server’s hostname in the “hello world” presented to the user 
•All AWS resources must be created using Terraform or CloudFormation
•No resources may be created or managed by hand other than EC2 SSH keys

