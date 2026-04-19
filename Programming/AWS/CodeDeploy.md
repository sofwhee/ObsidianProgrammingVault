CodeDeploy makes it easier for you to:

- Rapidly release new features.
- Update AWS Lambda function versions.
- Avoid downtime during application deployment.
- Handle the complexity of updating your applications, without many of the risks associated with error-prone manual deployments.

## Overview of CodeDeploy deployment types

CodeDeploy provides two deployment type options:

- **In-place deployment**: The application on each instance in the deployment group is stopped, the latest application revision is installed, and the new version of the application is started and validated. You can use a load balancer so that each instance is deregistered during its deployment and then restored to service after the deployment is complete. Only deployments that use the EC2/On-Premises compute platform can use in-place deployments. For more information about in-place deployments, see [Overview of an in-place deployment](https://docs.aws.amazon.com/codedeploy/latest/userguide/welcome.html#welcome-deployment-overview-in-place).
    
    ###### Note
    
    AWS Lambda and Amazon ECS deployments cannot use an in-place deployment type.
    
- **Blue/green deployment**: The behavior of your deployment depends on which compute platform you use:
    
    - **Blue/green on an EC2/On-Premises compute platform**: The instances in a deployment group (the original environment) are replaced by a different set of instances (the replacement environment) using these steps:
        
        - Instances are provisioned for the replacement environment.
            
        - The latest application revision is installed on the replacement instances.
            
        - An optional wait time occurs for activities such as application testing and system verification.
            
        - Instances in the replacement environment are registered with one or more Elastic Load Balancing load balancers, causing traffic to be rerouted to them. Instances in the original environment are deregistered and can be terminated or kept running for other uses.
            
        
        ###### Note
        
        If you use an EC2/On-Premises compute platform, be aware that blue/green deployments work with Amazon EC2 instances only.
        
    - **Blue/green on an AWS Lambda or Amazon ECS compute platform**: Traffic is shifted in increments according to a **canary**, **linear**, or **all-at-once** deployment configuration.
        
    - **Blue/green deployments through AWS CloudFormation**: Traffic is shifted from your current resources to your updated resources as part of an AWS CloudFormation stack update. Currently, only ECS blue/green deployments are supported.
        
    
    For more information about blue/green deployments, see [Overview of a blue/green deployment](https://docs.aws.amazon.com/codedeploy/latest/userguide/welcome.html#welcome-deployment-overview-blue-green).
### Overview of an in-place deployment

###### Note

AWS Lambda and Amazon ECS deployments cannot use an in-place deployment type.

Here's how an in-place deployment works:

1. First, you create deployable content on your local development machine or similar environment, and then you add an _application specification file_ (AppSpec file). The AppSpec file is unique to CodeDeploy. It defines the deployment actions you want CodeDeploy to execute. You bundle your deployable content and the AppSpec file into an archive file, and then upload it to an Amazon S3 bucket or a GitHub repository. This archive file is called an _application revision_ (or simply a _revision_).
    
2. Next, you provide CodeDeploy with information about your deployment, such as which Amazon S3 bucket or GitHub repository to pull the revision from and to which set of Amazon EC2 instances to deploy its contents. CodeDeploy calls a set of Amazon EC2 instances a _deployment group_. A deployment group contains individually tagged Amazon EC2 instances, Amazon EC2 instances in Amazon EC2 Auto Scaling groups, or both.
    
    Each time you successfully upload a new application revision that you want to deploy to the deployment group, that bundle is set as the _target revision_ for the deployment group. In other words, the application revision that is currently targeted for deployment is the target revision. This is also the revision that is pulled for automatic deployments.
    
3. Next, the CodeDeploy agent on each instance polls CodeDeploy to determine what and when to pull from the specified Amazon S3 bucket or GitHub repository.
    
4. Finally, the CodeDeploy agent on each instance pulls the target revision from the Amazon S3 bucket or GitHub repository and, using the instructions in the AppSpec file, deploys the contents to the instance.
    

CodeDeploy keeps a record of your deployments so that you can get deployment status, deployment configuration parameters, instance health, and so on.

### Overview of a blue/green deployment

A blue/green deployment is used to update your applications while minimizing interruptions caused by the changes of a new application version. CodeDeploy provisions your new application version alongside the old version before rerouting your production traffic.

- **AWS Lambda**: Traffic is shifted from one version of a Lambda function to a new version of the same Lambda function.
    
- **Amazon ECS**: Traffic is shifted from a task set in your Amazon ECS service to an updated, replacement task set in the same Amazon ECS service.
    
- **EC2/On-Premises**: Traffic is shifted from one set of instances in the original environment to a replacement set of instances.
    

All AWS Lambda and Amazon ECS deployments are blue/green. An EC2/On-Premises deployment can be in-place or blue/green. A blue/green deployment offers a number of advantages over an in-place deployment:

- You can install and test an application in the new replacement environment and deploy it to production simply by rerouting traffic.
    
- If you're using the EC2/On-Premises compute platform, switching back to the most recent version of an application is faster and more reliable. That's because traffic can be routed back to the original instances as long as they have not been terminated. With an in-place deployment, versions must be rolled back by redeploying the previous version of the application.
    
- If you're using the EC2/On-Premises compute platform, new instances are provisioned for a blue/green deployment and reflect the most up-to-date server configurations. This helps you avoid the types of problems that sometimes occur on long-running instances.
    
- If you're using the AWS Lambda compute platform, you control how traffic is shifted from your original AWS Lambda function version to your new AWS Lambda function version.
    
- If you're using the Amazon ECS compute platform, you control how traffic is shifted from your original task set to your new task set.
    

A blue/green deployment with AWS CloudFormation can use one of the following methods:

- **AWS CloudFormation templates for deployments**: When you configure deployments with AWS CloudFormation templates, your deployments are triggered by AWS CloudFormation updates. When you change a resource and upload a template change, a stack update in AWS CloudFormation initiates the new deployment. For a list of resources you can use in AWS CloudFormation templates, see [AWS CloudFormation templates for CodeDeploy reference](https://docs.aws.amazon.com/codedeploy/latest/userguide/reference-cloudformation-templates.html).
    
- **Blue/green deployments through AWS CloudFormation**: You can use AWS CloudFormation to manage your blue/green deployments through stack updates. You define both your blue and green resources, in addition to specifying the traffic routing and stabilization settings, within the stack template. Then, if you update selected resources during a stack update, AWS CloudFormation generates all the necessary green resources, shifts the traffic based on the specified traffic routing parameters, and deletes the blue resources. For more information, see [Automate Amazon ECS blue/green deployments through CodeDeploy using AWS CloudFormation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/blue-green.html) in the _AWS CloudFormation User Guide_.