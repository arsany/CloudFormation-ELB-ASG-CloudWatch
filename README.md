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
