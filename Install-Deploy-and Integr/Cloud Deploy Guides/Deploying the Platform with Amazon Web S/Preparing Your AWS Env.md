# Preparing Your AWS Environment

The goal of this topic is to provide you information on what is needed to establish an environment in which you can begin the deployment process. The checklist of needs include:

- Determining the AWS account into which the Profisee Platform will be deployed.
- Obtaining the account credentials you will need to access the account.
- Identifying the team members and subject matter experts that can perform, advise, and consult on the resources and network requirements for the deployment.
- Establishing a policy and role with permissions to perform and provision all the resources needed for the Profisee Platform deployment.
- Assigning team members the required roles to perform the deployment.
- Deciding on the deployment tooling and ensuring that team members have installed the tooling necessary for the deployment.

The following flow diagram outlines basic environmental setup process needed to complete this part of the planning cycle.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i76d4dc09826bdea0.png)

### Creating or Obtaining Your AWS Account Credentials

You or your company must establish an AWS account to deploy the Profisee Platform to AWS. If you do not already have an account, you can follow the instructions in [How do I create and activate a new AWS account?](https://aws.amazon.com/premiumsupport/knowledge-center/create-and-activate-aws-account/) on the Amazon web site.

If your company already has one or more accounts, you must have the administrator of the target account add you and other team members as authorized IAM users to the existing account. Refer to [Creating an IAM user in your AWS account](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html) for details on being added as a user.

### Identifying Your Deployment Team Members

Deploying enterprise-grade application like the Profisee Platform in the cloud can be a complex endeavor and may require interdepartmental skills and knowledge to accomplish. It is a good idea to make sure that you assemble the right cross-functional team in advance to ensure that requirements can be fully ascertained and that sound decisions are made prior to the execution of the deployment. The following cross-functional areas should be considered when establishing your deployment team:

- **Security and system access**. You should consult and engage with someone on your information security team that understands topics such as authentication and [Open ID Connect (OICD)](https://auth0.com/docs/protocols/openid-connect-protocol), encryption, authorization, fire walls, and network security to ensure all your access and communications are properly secured.
- **Database provisioning and performance**. Typically, you will want to engage with DBAs and database architects familiar with provisioning databases - specifically Microsoft SQL Server - in the AWS environment. These experts, along with Profisee Professional Services and Support, can help ensure the database is sized and resourced properly for your data and workload needs.
- **Networking and domain administration skills.** Deployment of the Profisee Platform involves several intra- and inter-cloud networking and routing considerations. You should ensure that your deployment team includes, or engages with, corporate networking experts when planning out your deployment strategy.

Although Profisee's Professional Services and Support teams are trained on the general procedures related to cloud deployments, many decisions and requirements to which organizations are bound involve resources, policies, and general institutional knowledge that is best obtained through corporate subject matter expertise. Thus, Profisee strongly encourages the cross-functional approach described above.

### Establishing Your IAM Policies and Permissions

Once you have identified your deployment team members, you must assign them the privileges they need to accomplish their specific assignments as it pertains to the deployment process. The following Amazon links detail the process of establishing the necessary permissions.

- The article [Minimum IAM policies](https://eksctl.io/usage/minimum-iam-policies/) describes a least-privileges approach to performing the most common use-cases related to creating and managing your EKS cluster.
- The article [What are the least privileges required for a user to perform creates, deletes, modifications, backup, and recovery for an Amazon RDS DB instance](https://aws.amazon.com/premiumsupport/knowledge-center/rds-iam-least-privileges/) covers the minimal requirements to provision and manage the database during a Profisee Platform deployment.

Profisee has verified that the policies and permissions guidance described in these articles allows you and your team to successfully manage the deployment process in most typical installations. Because there are virtually endless combinations deployment scenarios, the policy recommendations described above may need to be revisited based on your specific deployment needs and corporate security and networking requirements.

### Choosing & Installing Your Deployment Tooling

AWS offers two approaches for executing the commands necessary for deployment of the resources during the deployment of the Profisee Platform:

- The [AWS CloudShell](https://aws.amazon.com/cloudshell/) is a persistent, browser-based application that allows you to run a variety of underlying shells including Bash, PowerShell, and Zsh and works with various command line interfaces (CLIs) to manage resources securely in AWS. Although CloudShell comes with a variety of pre-installed commands and utilities, there are some utilities that are not included when the CloudShell is provisioned. The article [Setting up a working environment for Amazon EKS with AWS CloudShell](https://dev.to/aws-builders/setting-up-a-working-environment-for-amazon-eks-with-aws-cloudshell-1nn7) includes some additional guidance and setup steps you should perform before starting the actual deployment process using CloudShell.

As of the time of this writing, AWS CloudShell is relatively new and not available in all AWS regions. If this is not available in your region, use the AWS CLI approach outlined in the following bullet.

- The [AWS CLI](https://aws.amazon.com/cli/) and other related command line interfaces can be run on the team members' local machines assuming they have installed the required tools and have their associated [Identity and Access Management (IAM)](https://aws.amazon.com/iam/) permissions granted. The **AWS CLI** can be downloaded from [here](https://awscli.amazonaws.com/AWSCLIV2.msi). The following articles provide additional guidance around preparing a local workstation for working with AWS commands and resources:
- [Getting started with Amazon EKS - eksctl](https://docs.aws.amazon.com/eks/latest/userguide/eksctl.html)
- [The eksctl command line utility](https://docs.aws.amazon.com/eks/latest/userguide/eksctl.html)
- [Installing kubectl](https://docs.aws.amazon.com/eks/latest/userguide/install-kubectl.html)