# Summary

An [API, or application programming interface](https://www.ibm.com/topics/api), is a set of rules or protocols that enables software applications to communicate with each other to exchange data, features and functionality. A request for data from a client to an API is known as an API call.

An API gateway 
- receives an API call (sometimes called an API request)
- routes it to one or more backend services
- gathers the requested data from the backend
- delivers it to the client in a single, combined package
- (It also provides analytics, layers of threat protection and other security for the application)

For example, consider a restaurant’s web application. Using a laptop or cellphone, a user can enter one request and easily access the restaurant’s menu, photos and reviews, its payment service and a map to check its location, despite all that information being gathered and delivered from different backend microservices or APIs. The request submitted via the user’s application is received and executed by an API gateway.

An API gateway is an [API management](https://www.ibm.com/topics/api-management) tool that acts as an intermediary between an API client (the application on a user’s device) and backend services (located on a server). An API gateway presents a single point of entry for API calls.

Amazon API Gateway is an Amazon Web Services (AWS) feature that enables developers to connect non-AWS applications to AWS back-end resources, such as servers and code. 

The gateway increases AWS customers' access to compatible applications and the overall utility of Amazon's other cloud services.

An API Gateway is an interface that sits in between the application and the microservices. Developers use them to create, publish, maintain, monitor and secure APIs.

An API gateway can **secure traffic between API consumer requests and the execution of services**, protecting your organization against threats such as Denial of Service (DoS) attacks based on IP address, specific mobile devices or message volume.

Amazon API Gateway is an AWS service for creating, publishing, maintaining, monitoring, and securing REST, HTTP, and WebSocket APIs at any scale.

API Gateway creates RESTful APIs that:
- Are HTTP-based.
- Enable stateless client-server communication.
- Implement standard HTTP methods such as GET, POST, PUT, PATCH, and DELETE.
## The value of an API gateway

API gateways can be deployed in the [cloud](https://www.ibm.com/topics/cloud-computing), on-premises and in [hybrid](https://www.ibm.com/topics/hybrid-cloud) environments and are an important component of both API management and [API security](https://www.ibm.com/topics/api-security). API gateways help organizations provide a consistent, secure and satisfactory API experience for users.

API management is the scalable process of creating, publishing and managing APIs within an enterprise. API gateways improve and streamline management tasks such as request routing, [load balancing](https://www.ibm.com/topics/load-balancing) and error handling. API gateways also improve API [observability](https://www.ibm.com/topics/observability) by generating logs of API calls and enabling the use of integrated analytics tools.

API security refers to the practices and procedures that protect APIs from misuse, malicious attacks and other [cybersecurity](https://www.ibm.com/topics/cybersecurity) threats. API gateways help enforce API security protocols and can be used to manage authentication, authorization and other permissions and access controls (by confirming [API keys](https://www.ibm.com/topics/api-key), or integrating with authorization protocols such as OAuth, for example), rate limiting (to protect against attacks such as [distributed denial of service attacks](https://www.ibm.com/topics/ddos)) and encryption per an organization’s API security policies.

API gateways provide additional functions to enhance efficiency within an enterprise, helping enable high performance and high availability for applications and backend services. For example, API gateways can be used for caching, a process in which commonly referenced data is stored locally. This helps improve response time and reduces the load on servers. They can also compress large responses into smaller files, reducing bandwidth consumption.  
  
They also provide rate limiting capabilities, which sets a limit on how often a client can send a request to a service in a set amount of time. This promotes stability, prevents servers from becoming overloaded and helps ensure that clients have equal access to APIs.

API gateways and their capabilities help organizations balance API traffic and workloads as the organization scales. By centralizing these functions, API gateways help streamline how an enterprise develops, deploys and manages APIs. Gateways help improve the performance, scalability and availability of apps and services and enable developers to focus more on core business logic rather than API administration.

![3D design of balls rolling on a track](https://www.ibm.com/content/dam/connectedassets-adobe-cms/worldwide-content/pm/ul/g/5a/6e/trailv2_1200x1200.component.think-ad-xl.ts=1735835445257.jpeg/content/experience-fragments/adobe-cms/us/en/site-v2/think-hub/article/_8_column_general_ad/blueprint---think-ad---xf---do-not-modify/artificialintelligence-article-newsletter/_jcr_content/root/think_ad_copy/image)

### The latest AI News + Insights  

Discover expertly curated insights and news on AI, cloud and more in the weekly Think Newsletter. 

[Subscribe today](https://www.ibm.com/account/reg/signup?formid=news-urx-52954)

## How does an API gateway work?

APIs enable applications to communicate with each other and share data both within and outside of an organization’s IT environment. Modern enterprises can have thousands of APIs and a gateway provides a central focal point—a “front door”—and standardized interface that helps manage and route API calls from one location. An organization might choose to use multiple gateways, as many do, to allow for different security protocols and standards to be applied to different APIs or users, but the same principles apply.  

### Requests and routing

An API gateway receives all the calls directed at an enterprises [API endpoints](https://www.ibm.com/topics/api-endpoint), authenticates the calls, processes them based on organizational policies, routes them to the appropriate services, then finally aggregates and returns the results to the API client that made the call. Even if multiple services are requested and accessed through the API call, the client only receives one response with all the data.

### API composition

An API gateway provides workflow orchestration as it aggregates the requested information from multiple microservices, bundles the data and returns it to the requestor in composite form.

### Protocol and data translation

An API gateway handles data and protocol translation in cases where the client device and microservices use different languages, formats (say, the request comes in using JavaScript or JSON but the microservice uses XML) or protocols (such as HTTP requests versus gRPC requests).

### Caching

For commonly requested information, API gateways might use caching to accelerate the response time for the request. This data is stored in a separate cache so that the gateway can quickly return it without needing to route traffic to an additional service.

### Monitoring and logging

API gateways can monitor and log API requests, responses and errors. This analytics data can be used to gain a better understanding of API traffic and performance, improve troubleshooting and strengthen security.

AI Academy

![Achieving AI-readiness with hybrid cloud](https://cdnsecakmi.kaltura.com/p/1773841/thumbnail/entry_id/1_imy3p6x3/width/555)

### Achieving AI-readiness with hybrid cloud

Led by top IBM thought leaders, the curriculum is designed to help business leaders gain the knowledge needed to prioritize the AI investments that can drive growth.

[Go to episode](https://www.ibm.com/think/videos/ai-academy/hybrid-cloud-ai) 

## Why use an API gateway?

APIs are crucial to the flow of data in modern systems and API gateways help protect APIs and applications, help organizations gather valuable data and help ensure API performance.

API gateways can make processes more efficient. All of an organization’s APIs might need to complete a few common tasks alongside their specific function every time a call to that API is made. In an API-first ecosystem, where APIs are the building blocks upon which software is built, this is especially common.

For example, to comply with API security protocols, every API call might need to go through an authorization and validation process. Or to help ensure adequate bandwidth, every API might need to be monitored for usage rates and traffic. If APIs are monetized, every call might need to be routed to a billing service. An API gateway can handle all these tasks.

Some API calls require resources from several different [microservices](https://www.ibm.com/topics/microservices); an API gateway breaks down such calls, routes the requests to the appropriate backend services and aggregates the requested resources into one response for the client. This prevents the client from having to send a separate API call to each microservice, streamlining the process and reducing call load. Calls always go to the same place and the gateway organizes resource retrieval and return.

This capability is particularly beneficial in a [DevOps](https://www.ibm.com/topics/devops) environment, where microservices architectures are often used to help teams accelerate development and continuously deliver new apps and services. Microservices rely on APIs to communicate and gateways can be used to orchestrate this communication. An API gateway can also help ensure that each call is going to the correct place when multiple versions of an application are on the same server.

API gateways are also used in [serverless computing](https://www.ibm.com/topics/serverless) models and other cloud-native-development approaches. In a serverless model, infrastructure and other backend services are run on-demand and spun up using APIs. Gateways can be used to manage this function.

Modern IT environments are all about integration, the success of which relies in large part on APIs. The more complex an API environment and the greater the traffic APIs receive, the more value an API gateway can provide.

## API gateways and microservices

A [microservices](https://www.ibm.com/think/topics/soa-vs-microservices) architecture is a software development approach in which applications are composed of smaller, independently functioning parts. These distinct functions can be deployed autonomously and communicate via APIs. They are designed to fulfill a singular goal, with the intention of being grouped together as the building blocks of larger programs.

Routing calls from API clients to these individual microservices is possible, but it is not very efficient and would require a separate call for each resource. An API gateway enables an organization to return the requested resources with a single API call.

It works like this: The gateway receives the API call that requires communication with several microservices. It breaks up the request, routes each segment to the appropriate resources and aggregates the resources into a single response for the API client. As an organization increases the number of APIs and microservices used in business functions, an API gateway helps reduce call volume and the complexity of routing calls by acting as a standardized, single-entry point.

Let’s imagine a client wants to pull product information from an ecommerce store built using a microservices architecture. The product details that the client wants to pull are spread out over multiple different services—a service for basic product information, a service for pricing, a service for inventory and so on.

The API gateway receives the request for product information, routes it to pull data from each service required to fulfill the request and then compiles that data and sends it back to the client as one complete response.

## API gateways and Kubernetes

[Kubernetes](https://www.ibm.com/topics/kubernetes) is considered the industry standard for deploying and managing containerized microservices. API gateways can interact with a containerized Kubernetes cluster in multiple ways.

When deployed in front of more than one Kubernetes cluster, an API gateway can serve as a load balancer, directing traffic to the correct cluster so that no one instance is overloaded. When deployed at the edge of a singular Kubernetes cluster, an API gateway can act as an ingress controller. Ingress controllers direct traffic into a Kubernetes cluster, to the requested services and then back out again. When deployed within a Kubernetes cluster, an API gateway can act as a service mesh. A service mesh handles traffic flowing between Kubernetes services, offering load balancing and service discovery and is commonly used for end-to-end encryption.

## How does an API gateway improve API management

Beyond enabling organizations to route and balance API traffic more effectively, API gateways strengthen API management by helping:

- Lower latency
- Increase security
- Reduce complexity

### Lower latency

API gateways can help optimize traffic routing and load balancing across backend services by managing API calls through a centralized entry point. Such measures help maintain low [latency.](https://www.ibm.com/topics/latency) API gateways use a variety of methods for API traffic management that use bandwidth more efficiently and improve the user experience.

One such method is rate limiting. Rate limiting policies specify the number of requests (a request quota) that a specific client can make to an API over specific period of time. This helps make sure that users have equal access to APIs and protects backend services from becoming overloaded with requests.

Request throttling is a type of limiting that regulates the rate of requests that is hitting a server. This prevents spikes and helps organizations maintain performance and stability.

API gateways can also perform dynamic load balancing by continuously monitoring traffic to backend services. An API gateway can determine the health of a server based on real-time metrics and adjust how it routes calls to backend services.

### Increase security

APIs are vulnerable to cybersecurity attacks such as distributed denial of service (DDoS) attacks. DDoS attacks overload servers with requests and malicious traffic, causing them to crash. An API gateway supports rate limiting and other techniques to help thwart DDoS attacks.  
  
API gateways can also help secure APIs by monitoring API usage and providing traffic logs. Some API gateways also provide reports and analytics about the requests being made to any APIs in an organization’s infrastructure, enabling an organization to identify suspicious traffic before an attack happens.

API gateways not only assist in traffic management and provide a secure connection to APIs but can also be configured to provide API authentication and request authorization, reducing the vulnerability of an organization’s APIs. For example, API gateways are used to verify API keys when calls are received from a client before granting access to resources. For greater security, API gateways can be used in conjunction with tools such as web application firewalls (WAF), which monitor, filter and block malicious HTTP traffic.

### Reduce complexity

API gateways centralize the flow of API calls, improving service visibility and discoverability. They also provide ways for APIs that use different protocols and data formats to communicate with each other.

Many web APIs use an architectural style called REST (representational state transfer, used in [REST APIs](https://www.ibm.com/topics/rest-apis)), though other protocols, such as SOAP (simple object access protocol) and WebSocket APIs are also used. Whether it’s within an organization, or external calls directed at an organization’s internal APIs, it’s common to have APIs with various protocols and data formats that need to communicate with each other and request resources from the same backend services.

Manually converting each request would take an astronomical amount of time; API gateways help eliminate this problem by performing data and protocol translation, automatically translating requests and responses into the necessary format.

API gateways also make it easier for developers to iterate upon and deploy APIs because gateways can manage multiple versions of an API at the same time. Developers can then test multiple versions of an API against each other before deployment or maintain an instance of an older API version for specific use cases.  

### Additional API benefits include:

- **Extending legacy apps:** Businesses still use legacy applications that contain essential data, perform significant functions and provide value, but the apps were not written for APIs. Such older technology can have trouble handling the increasing numbers of calls from newer technologies, such as mobile, [SaaS](https://www.ibm.com/topics/saas) or [IoT](https://www.ibm.com/topics/internet-of-things) apps. They can also be hard to access. Instead of taking on a complicated [cloud migration](https://www.ibm.com/topics/cloud-migration), a DevOps team can add API functionality—including benefits such as rate limiting and throttling—to help modernize and extend the functionality of a legacy application.  
      
    
- **Microservices caching:** API gateways can help optimize API calls, such as with microservices caching. Caching responses to API calls can help avoid unnecessary load on backend services. The cached responses can be used when similar requests are received, improving performance and decreasing cost.  
      
    
- **Monitoring and tracking [application analytics](https://www.ibm.com/think/topics/ai-for-saas-analytics):** Since an API gateway controls all an application’s inbound traffic, it’s straightforward to have the software monitor and produce reports about visibility, trends and other insights about API usage. The gateway software can also create traffic logs that help an API provider understand and fix infrastructure problems.

## API gateway challenges

While API gateways can help resolve complicated routing issues, adding a new piece of management software to any organization can also introduce new challenges. Common challenges include:

- Scalability issues
- Single point of failure
- Gateway dependency/vendor lock-in  
    

### Scalability issues

While API gateways can help organize API infrastructure and lower latency, if they receive more requests than they are configured to manage and don’t have enough resources to handle the traffic, they can increase latency instead.

Organizations must make sure that API gateways are provisioned and configured to meet the API environment and traffic demands of the enterprise. As an enterprise increases the amount APIs and services in use at any given time, resources must be scaled and [provisioned](https://www.ibm.com/topics/provisioning) accordingly to prevent users from experiencing any interruptions in service.

### Single point of failure

A single point of entry also means that there can be a single point of failure. Centralizing APIs has a tremendous number of upsides, but the downside is that the gateway itself becomes a potential vector for an attack or infiltration. Gateway issues can have effects on all aspects of an enterprise that rely on access to APIs and backend services.

### Gateway dependency

Once an organization has chosen the API gateway that meets their specific needs and built their API environment around that gateway, it can be expensive and time-consuming to move to another vendor.

Additionally, while gateways can make API usage more cost effective, the gateway will also require monitoring and management, which costs time and money. In some cases, an organization might choose to self-host an open-source gateway, rather than using a managed service, to have finer control over its various options. If an organization chooses a self-hosted option, this will add to the overall overhead costs for the development team.
## Use API Gateway to create REST APIs

An API Gateway REST API is made up of resources and methods. A resource is a logical entity that an app can access through a resource path. A method corresponds to a REST API request that is submitted by the user of your API and the response returned to the user.

For example, `/incomes` could be the path of a resource representing the income of the app user. A resource can have one or more operations that are defined by appropriate HTTP verbs such as GET, POST, PUT, PATCH, and DELETE. A combination of a resource path and an operation identifies a method of the API. For example, a `POST /incomes` method could add an income earned by the caller, and a `GET /expenses` method could query the reported expenses incurred by the caller.

The app doesn't need to know where the requested data is stored and fetched from on the backend. In API Gateway REST APIs, the frontend is encapsulated by _method requests_ and _method responses_. The API interfaces with the backend by means of _integration requests_ and _integration responses_.

For example, with DynamoDB as the backend, the API developer sets up the integration request to forward the incoming method request to the chosen backend. The setup includes specifications of an appropriate DynamoDB action, required IAM role and policies, and required input data transformation. The backend returns the result to API Gateway as an integration response.

To route the integration response to an appropriate method response (of a given HTTP status code) to the client, you can configure the integration response to map required response parameters from integration to method. You then translate the output data format of the backend to that of the frontend, if necessary. API Gateway enables you to define a schema or model for the [payload](https://en.wikipedia.org/wiki/Payload_(computing))  to facilitate setting up the body mapping template.

API Gateway provides REST API management functionality such as the following:

- Support for generating SDKs and creating API documentation using API Gateway extensions to OpenAPI
    
- Throttling of HTTP requests
    

## Use API Gateway to create HTTP APIs

HTTP APIs enable you to create RESTful APIs with lower latency and lower cost than REST APIs.

You can use HTTP APIs to send requests to AWS Lambda functions or to any publicly routable HTTP endpoint.

For example, you can create an HTTP API that integrates with a Lambda function on the backend. When a client calls your API, API Gateway sends the request to the Lambda function and returns the function's response to the client.

HTTP APIs support [OpenID Connect](https://openid.net/developers/how-connect-works/) and [OAuth 2.0](https://oauth.net/2/) authorization. They come with built-in support for cross-origin resource sharing (CORS) and automatic deployments.

To learn more, see [Choose between REST APIs and HTTP APIs](https://docs.aws.amazon.com/apigateway/latest/developerguide/http-api-vs-rest.html).

## Use API Gateway to create WebSocket APIs

In a WebSocket API, the client and the server can both send messages to each other at any time. Backend servers can easily push data to connected users and devices, avoiding the need to implement complex polling mechanisms.

For example, you could build a serverless application using an API Gateway WebSocket API and AWS Lambda to send and receive messages to and from individual users or groups of users in a chat room. Or you could invoke backend services such as AWS Lambda, Amazon Kinesis, or an HTTP endpoint based on message content.

You can use API Gateway WebSocket APIs to build secure, real-time communication applications without having to provision or manage any servers to manage connections or large-scale data exchanges. Targeted use cases include real-time applications such as the following:

- Chat applications
    
- Real-time dashboards such as stock tickers
    
- Real-time alerts and notifications
    

API Gateway provides WebSocket API management functionality such as the following:

- Monitoring and throttling of connections and messages
    
- Using AWS X-Ray to trace messages as they travel through the APIs to backend services
    
- Easy integration with HTTP/HTTPS endpoints
    

## Who uses API Gateway?

There are two kinds of developers who use API Gateway: API developers and app developers.

An API developer creates and deploys an API to enable the required functionality in API Gateway. The API developer must be a user in the AWS account that owns the API.

An app developer builds a functioning application to call AWS services by invoking a WebSocket or REST API created by an API developer in API Gateway.

The app developer is the customer of the API developer. The app developer doesn't need to have an AWS account, provided that the API either doesn't require IAM permissions or supports authorization of users through third-party federated identity providers supported by [Amazon Cognito user pool identity federation](https://docs.aws.amazon.com/cognito/latest/developerguide/). Such identity providers include Amazon, Amazon Cognito user pools, Facebook, and Google.

### Creating and managing an API Gateway API

An API developer works with the API Gateway service component for API management, named `apigateway`, to create, configure, and deploy an API.

As an API developer, you can create and manage an API by using the API Gateway console, described in [Get started with API Gateway](https://docs.aws.amazon.com/apigateway/latest/developerguide/getting-started.html), or by calling the [API references](https://docs.aws.amazon.com/apigateway/latest/developerguide/api-ref.html). There are several ways to call this API. They include using the AWS Command Line Interface (AWS CLI), or by using an AWS SDK. In addition, you can enable API creation with [AWS CloudFormation templates](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/template-reference.html) or (in the case of REST APIs and HTTP APIs) [OpenAPI extensions for API Gateway](https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-swagger-extensions.html).

For a list of Regions where API Gateway is available, as well as the associated control service endpoints, see [Amazon API Gateway Endpoints and Quotas](https://docs.aws.amazon.com/general/latest/gr/apigateway.html).

### Calling an API Gateway API

An app developer works with the API Gateway service component for API execution, named `execute-api`, to invoke an API that was created or deployed in API Gateway. The underlying programming entities are exposed by the created API. There are several ways to call such an API. To learn more, see [Invoke REST APIs in API Gateway](https://docs.aws.amazon.com/apigateway/latest/developerguide/how-to-call-api.html) and [Invoke WebSocket APIs](https://docs.aws.amazon.com/apigateway/latest/developerguide/apigateway-how-to-call-websocket-api.html).

# Make an API Gateway

![[Pasted image 20250115142643.png]]

- [Step 1: Create a Lambda function](https://docs.aws.amazon.com/apigateway/latest/developerguide/getting-started.html#getting-started-create-function)
- [Step 2: Create an HTTP API](https://docs.aws.amazon.com/apigateway/latest/developerguide/getting-started.html#getting-started-create-api)
- [Step 3: Test your API](https://docs.aws.amazon.com/apigateway/latest/developerguide/getting-started.html#getting-started-invoke-api)
- [(Optional) Step 4: Clean up](https://docs.aws.amazon.com/apigateway/latest/developerguide/getting-started.html#getting-started-cleanup)

## Step 1: Create a Lambda function

You use a Lambda function for the backend of your API. Lambda runs your code only when needed and scales automatically, from a few requests per day to thousands per second.

For this example, you use the default Node.js function from the Lambda console.
###### To create a Lambda function
1. Sign in to the Lambda console at [https://console.aws.amazon.com/lambda](https://console.aws.amazon.com/lambda).
2. Choose **Create function**.
3. For **Function name**, enter `my-function`.
4. For all other options, use the default setting.
5. Choose **Create function**.

The example function returns a `200` response to clients, and the text `Hello from Lambda!`.

The default Lambda function code should look similar to the following:

```javascript
export const handler = async (event) => {
    const response = {
        statusCode: 200,
        body: JSON.stringify('Hello from Lambda!'),
    };
    return response;
};
```

## Step 2: Create an HTTP API

Next, you create an HTTP API. API Gateway also supports REST APIs and WebSocket APIs, but an HTTP API is the best choice for this exercise. REST APIs support more features than HTTP APIs, but we don't need those features for this exercise. HTTP APIs are designed with minimal features so that they can be offered at a lower price. WebSocket APIs maintain persistent connections with clients for full-duplex communication, which isn't required for this example.

The HTTP API provides an HTTP endpoint for your Lambda function. API Gateway routes requests to your Lambda function, and then returns the function's response to clients.

###### To create an HTTP API
1. Sign in to the API Gateway console at [https://console.aws.amazon.com/apigateway](https://console.aws.amazon.com/apigateway).
2. Do one of the following:
    - To create your first API, for **HTTP API**, choose **Build**.
    - If you've created an API before, choose **Create API**, and then choose **Build** for **HTTP API**.
3. For **Integrations**, choose **Add integration**.
4. Choose **Lambda**.
5. For **Lambda function**, enter `my-function`.
6. For **PI name**, enter `my-http-api`.
7. Choose **Next**.
8. Review the _route_ that API Gateway creates for you, and then choose **Next**.
9. Review the _stage_ that API Gateway creates for you, and then choose **Next**.
10. Choose **Create**.

Now you've created an HTTP API with a Lambda integration that's ready to receive requests from clients.
## Step 3: Test your API

Next, you test your API to make sure that it's working. For simplicity, use a web browser to invoke your API.

###### To test your API

1. Sign in to the API Gateway console at [https://console.aws.amazon.com/apigateway](https://console.aws.amazon.com/apigateway).
    
2. Choose your API.
    
3. Note your API's invoke URL.
    
    ![After you create your API, the console shows your API's invoke URL.](https://docs.aws.amazon.com/images/apigateway/latest/developerguide/images/getting-started-invoke-url.png)
    
4. Copy your API's invoke URL, and enter it in a web browser. Append the name of your Lambda function to your invoke URL to call your Lambda function. By default, the API Gateway console creates a route with the same name as your Lambda function, `my-function`.
    
    The full URL should look like `` https://`abcdef123`.execute-api.`us-east-2`.amazonaws.com/`my-function` ``.
    
    Your browser sends a `GET` request to the API.
    
5. Verify your API's response. You should see the text `"Hello from Lambda!"` in your browser.
## (Optional) Step 4: Clean up

To prevent unnecessary costs, delete the resources that you created as part of this getting started exercise. The following steps delete your HTTP API, your Lambda function, and associated resources.

###### To delete an HTTP API

1. Sign in to the API Gateway console at [https://console.aws.amazon.com/apigateway](https://console.aws.amazon.com/apigateway).
    
2. On the **APIs** page, select an API. Choose **Actions**, and then choose **Delete**.
    
3. Choose **Delete**.
    

###### To delete a Lambda function

1. Sign in to the Lambda console at [https://console.aws.amazon.com/lambda](https://console.aws.amazon.com/lambda).
    
2. On the **Functions** page, select a function. Choose **Actions**, and then choose **Delete**.
    
3. Choose **Delete**.
    

###### To delete a Lambda function's log group

1. In the Amazon CloudWatch console, open the [Log groups page](https://console.aws.amazon.com/cloudwatch/home#logs:).
    
2. On the **Log groups** page, select the function's log group (`/aws/lambda/my-function`). Choose **Actions**, and then choose **Delete log group**.
    
3. Choose **Delete**.
    

###### To delete a Lambda function's execution role

1. In the AWS Identity and Access Management console, open the [Roles page](https://console.aws.amazon.com/iam/home?#/roles).
    
2. Select the function's role, for example, `` my-function-`31exxmpl` ``.
    
3. Choose **Delete role**.
    
4. Choose **Yes, delete**.
    

You can automate the creation and cleanup of AWS resources by using AWS CloudFormation or AWS SAM. For example AWS CloudFormation templates, see [example AWS CloudFormation templates](https://github.com/awsdocs/amazon-api-gateway-developer-guide/tree/main/cloudformation-templates).

# Develop HTTP APIs in API Gateway
https://docs.aws.amazon.com/apigateway/latest/developerguide/http-api-develop.html