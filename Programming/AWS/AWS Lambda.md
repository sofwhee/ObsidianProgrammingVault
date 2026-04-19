You can use AWS Lambda to run code without provisioning or managing servers.
## Understanding serverless

To understand what AWS Lambda is, we have to first understand what serverless architecture is all about. Serverless applications in general are applications that don’t require any provisioning of servers for them to run. When you run a serverless application, you get the benefit of not worrying about OS setup, patching, or scaling of servers that you would have to consider when you run your application on a physical server.

Serverless applications or platforms have four characteristics:

1. No server management
2. Flexible scaling
3. No idle capacity
4. High availability

Serverless applications have several components and layers:

- Compute
- API
- Storage
- Interprocess Messaging
- Orchestration

As a cloud provider, AWS offers services that can be used for each of these components that make up a serverless architecture. This is where AWS Lambda comes in.

## Describing AWS Lambda

AWS Lambda service is a high-scale, provision-free [serverless compute](https://aws.amazon.com/lambda/) offering based on [functions](https://www.webopedia.com/TERM/F/function.html). It is used _only_ for the compute layer of a serverless application. The purpose of AWS Lambda is to build event-driven applications that can be triggered by several events in AWS.

In the case where you have multiple simultaneous events, Lambda simply spins up multiple copies of the function to handle the events. In other words, Lambda can be described as a type of function as a service ([FaaS](https://www.bmc.com/blogs/serverless-faas/)). Three components comprise AWS Lambda:

- **A function.** This is the actual code that performs the task.
- **A configuration.** This specifies how your function is executed.
- **An event source (optional).** This is the event that triggers the function. You can trigger with several AWS services or a third-party service.

When you specify an event source, your function is invoked when an event from that source occurs. The diagram below shows what this looks like:

![[Pasted image 20250115163633.png]]
## Running a Lambda function

When configuring a lambda function, you specify which **runtime environment** you’d like to run your code in. Depending on the language you use, each environment provides its own set of binaries available for use in your code. You are also allowed to package any libraries or binaries you like as long as you can use them within the runtime environment. All environments are based on Amazon Linux AMI.

The current available runtime environments are:

- nodeJS
- Python
- Go
- Java
- Ruby
- .Net
- C#

When running a lambda function, we only focus on the code because AWS manages capacity and all updates. AWS Lambda can be invoked synchronously using the **ResponseRequest InvocationType** and asynchronously using the **EventInvocationType**.
## Concepts of Lambda function

To better understand how lambda function works, there are key concepts to understand.

![](https://s7280.pcdn.co/wp-content/uploads/2020/03/key-feature-lamba-functions-1024x749.png)

## Event source

Although AWS Lambda can be triggered using the Invoke API, the recommended way of triggering lambda is through event sources from within AWS.

There are two models of invocation supported:

(a) **Push** which get triggered by other events such as API gateway, new object in S3 or Amazon Alexa.

(b) **Pull** where the lambda function goes and poll an event source for new objects. Examples of such event sources are DynamoDB or Amazon Kinesis.
## Lambda configuration

There are few configuration settings that can be used with lambda functions:

- **Memory dial** which controls not just the memory but also affects how much CPU and network resources is allocated to the function.
- **Version/Aliases** are used to revert function back to older versions. This is also key in implementing a deployment strategy such as blue/green or separating production from lower environments.
- **IAM Role** gives the lambda function permission to interact with other AWS services and APIs.
- **Lambda function permission** defines which push model event source is allowed to invoke the lambda function.
- **Network configuration for outbound connectivity**. There are two choices:
    - _Default_ which allows internet connectivity but no connectivity to private resources in your VPC services
    - _VPC_ which allows your function to be provisioned inside your VPC and use an [ENI](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-eni.html). You can then attach things like security like you would any other ENIs.
- **Environment variables** for dynamically injecting values that are consumed by code. This idea of separating code from config is one of the [12-factor app methodology](https://www.bmc.com/blogs/twelve-factor-app/) around cloud native applications.
- **Dead letter queue** is where you send all failed invocation events. This can either be [SNS](https://aws.amazon.com/sns/?whats-new-cards.sort-by=item.additionalFields.postDateTime&whats-new-cards.sort-order=desc) topic or [SQS](https://aws.amazon.com/sqs/)

**Timeouts** which is the allowed amount of time a function is allowed to run before it is timed out.

## Create an AWS Lambda

There are few ways to create a lambda function in AWS, but the most common way to create it is with the console but this method should only be used if testing in dev. For production, it is best practice to automate the deployment of the lambda.

There are few third-party tools to set up automation, like Terraform, but since we are specifically talking about an AWS service, AWS recommends using [Serverless Application Model (SAM)](https://www.bmc.com/blogs/aws-serverless-applications/) for this task. SAM is pretty much built [on top of](https://aws.amazon.com/cloudformation/) AWS CloudFormation and the template looks like a normal CloudFormation template except it has a transform block that specifically says we want the template to be a SAM template as opposed to a normal CloudFormation template. You can take a look at some example templates in the [AWSlabs](https://github.com/awslabs/serverless-application-model).
## When to use Lambda

Lambda is an ideal compute service for application scenarios that need to scale up rapidly, and scale down to zero when not in demand. For example, you can use Lambda for:

**File processing:** 
- Use Amazon Simple Storage Service (Amazon S3) to trigger Lambda data processing in real time after an upload.
**Stream processing:** 
- Use Lambda and Amazon Kinesis to process real-time streaming data for application activity tracking, transaction order processing, clickstream analysis, data cleansing, log filtering, indexing, social media analysis, Internet of Things (IoT) device data telemetry, and metering.
**Web applications:** 
- Combine Lambda with other AWS services to build powerful web applications that automatically scale up and down and run in a highly available configuration across multiple data centers.
**IoT backends:** 
- Build serverless backends using Lambda to handle web, mobile, IoT, and third-party API requests.
**Mobile backends:** 
- Build backends using Lambda and Amazon API Gateway to authenticate and process API requests. Use AWS Amplify to easily integrate with your iOS, Android, Web, and React Native frontends.

When using Lambda, you are responsible only for your code. Lambda manages the compute fleet that offers a balance of memory, CPU, network, and other resources to run your code. Because Lambda manages these resources, you cannot log in to compute instances or customize the operating system on provided runtimes. Lambda performs operational and administrative activities on your behalf, including managing capacity, monitoring, and logging your Lambda functions.

The Lambda service runs your function only when needed and scales automatically. You only pay for the compute time that you consume—there is no charge when your code is not running. For more information, see [AWS Lambda Pricing](https://aws.amazon.com/lambda/pricing/).

Lambda functions can connect to Amazon EFS file systems. However, Amazon EFS file system changes cannot invoke Lambda functions.

Lambda functions can be invoked from S3 events and can read from S3 buckets. An event-based invocation would allow for the S3 objects to be processed as soon as they arrive.

You can use an AWS Lambda function to process records in an [Amazon DynamoDB stream](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Streams.html). With DynamoDB Streams, you can trigger a Lambda function to perform additional work each time a DynamoDB table is updated.

## Alias

You can create aliases for your Lambda function.

A Lambda alias is a pointer to a function version that you can update. The function's users can access the function version using the alias Amazon Resource Name (ARN). When you deploy a new version, you can update the alias to use the new version, or split traffic between two versions.

## Environment Variables

To increase security, we recommend that you use AWS Secrets Manager instead of environment variables to store database credentials and other sensitive information like API keys or authorization tokens. For more information, see [Create and manage secrets with AWS Secrets Manager](https://docs.aws.amazon.com/secretsmanager/latest/userguide/managing-secrets.html).
## Simultaneous readers of a shard in DynamoDB Streams

For single-Region tables that are not global tables, you can design for up to two Lambda functions to read from the same DynamoDB Streams shard at the same time. Exceeding this limit can result in request throttling. For global tables, we recommend you limit the number of simultaneous functions to one to avoid request throttling.

## Event Source Mapping

An _event source mapping_ is a Lambda resource that reads items from stream and queue-based services and invokes a function with batches of records.