# notes from practice exam

differentiate between CAF (cloud Adoption Framework) and well architected framework

An IAM role that you assign to an EC2 instance is an instance profile. You can associate IAM policies with the role. The IAM policies grant the instance access to the AWS services that you define in the policy.

You can use access keys to write data from EC2 instances to an S3 bucket. However, access keys are long-term credentials.

what? Zone security controls are customer controls. Customers may need to route or zone data within specific security environments.

details about  AWS Trusted Advisor checks
it checks for S3 bucket permissions in Amazon S3 with open access permissions

AWS shared responsibility model confuses

Global Accelerator uses the AWS global network to route traffic to the optimal regional endpoint based on application health, client location, and other custom configurations. Global Accelerator helps to increase the availability and performance of applications hosted in AWS.

CloudHSM helps you comply with corporate, contractual, and regulatory compliance requirements for data security by using dedicated hardware security module (HSM) appliances within the AWS Cloud.

Systems Manager is used to organize, monitor, and automate management tasks on AWS resources. Systems Manager does not provide encryption for CloudTrail.

AWS KMS can be used to enable server-side encryption of CloudTrail data. AWS KMS makes it easy to create and manage cryptographic keys and control their use across a wide range of AWS services.

AWS WAF gives you control over how traffic reaches your applications. AWS WAF gives you the ability to create security rules that control network traffic and block common attack patterns. You can create an AWS WAF rule that filters traffic that has possibly malicious SQL code. This rule would prevent SQL injection attacks.

CloudFormation gives you the ability to reuse templates to set up resources consistently and repeatedly in multiple Regions.