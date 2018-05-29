# Self-service development portal- Project for Facilities Mgmt SW company
* All files are from "Advanced AWS CloudFormation" course by Adrian (5-start course!).
* Purpose: To allow the developers/pre-sale/QA to deploy a specific version of application into its own dedicated application environment. Optionally, to provide access to the environment to customers.
* It does not require access to AWS console. Staff can deploy application environment without requiring access to AWS console. They can browse webpage, click button then have a fully functioned provisioned application environment available in 10 minutes. They can delete the environment in the same portal page.  

## Requirements:
* Long term: automate provision within SaaS environment.
* Short term: automate testing and pre sale.

## Shared infrastructure-- provide network resources(assumed by application stack) necessary to deploy in application environment.
* VPC having assigned CIDR Range.
* VPC has external/public(it has a public shared infrastructure subnet in each AZ) and internal/private
* VPC has Internet gateway, public subnet has default route associated and pointing to the internet gateway.
* Within the public shared infrastructure subnet, we create pair of NAT gateway (manage product which provide internet access to any machine within the VPC, which do not have the direct public access, essentially any private instances.)
* Each NAT gateway needs elastic IP.   

## Application Environment
* Create pair of public subnets using IP ranges which were imported as the template parameters.
* Into each of the public subnet, elastic load balancer(ELB) instances are added. While there is one logical load balancer, it adds at least one node to each subnet. ELB will be the public end for application.
* Create two private subnets, which route out the internet with the shared infrastructure VPC. Inside each subnet, EC2 instance is created. It hosts the application using this application environment stack.
* Launch configuration will be used as configuration elements for autoscaling group, which will define subnet to use, min/max/desired number of instances and link with load balancers, so that any instances created or destroyed by autoscaling group will automatically register or removed from load balancer. Load balancer is created by cloudformation template for the application environment.

## Customer Resources using Lambda
* Custom Resource from AppEnv stack will invoke Lambda function.
* AutoSubnet stack will create Dynamodb table to store all CIDR locations.
* AutoSubnet Lambda will receive create request, then search through all available CIDR subnet range.
