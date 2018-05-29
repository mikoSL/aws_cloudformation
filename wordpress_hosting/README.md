# Steps for this project
* All files are from "Advanced AWS CloudFormation" course by Adrian (5-start course!).
* 1. provisonbucket.yml -- create two s3 buckets, one for resource, the other for portal.
* 2. stackrole.yml -- create a role which is applied to customer stacks.It allows customers, who has no access right to their own,  to interact with the stack and reconfigure aws resource.
* 3. customeriamandrole.yml -- customer role will be used by customers indirectly when they login through the self-service portal using their google username. When login, it authenticates with google, they receive google authentication token, aws cognito service will exchange this token for setting temporary credentials, which is based on security policy these customers have.
* 4. supportiam.yml -- support team who should create stack when customer requests.
* 5. Congnito configuration (manually)-- AWS Congnito is service to offer arbitration between web identities and aws access credentials.

# Results of the project.
* Support team can build stack directly from portal when customer requires.
* Customers have the access/delete right for the stacks from web portal. But no access when they log into the CloudFormation AWS console.
