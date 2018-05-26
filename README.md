# AWS CloudFormation
It is from the tutorials of A cloud guru Ltd.
* "AWS CloudFormation" course by Fernando Honig.
* "Advanced AWS CloudFormation" course by Adrian (5-start course!).
* "AWS CodeDeploy" by Alex Glover.

## create-s3-bucket.json
* create a new s3 bucket and AWS assigns name to it randomly.

## update-s3-bucket.json
* create a new s3 bucket and pre-define name for it.

## create-vpc.json
* 1 VPC
* 4 subnets (2 on each az)
* 3 route tables
* 1 internet gateway
* 2 NAT gateway (1 on each az)
* 2 elastic IPs (1 for each NAT gateway)

## create-codedeploy-infra.json
* codedeploy infrastructure setup

## workpress-hosting project
### Background:
* WordPress hosting website is build on LAMP stacks.

### Purposes:
* automatically install and configure Wordpress.
* end2end, 1-click deployment & self-service portal.
* serve global large and small customers.
