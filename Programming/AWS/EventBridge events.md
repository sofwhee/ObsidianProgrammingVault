An _event_ indicates a change in an environment such as an AWS environment, a SaaS partner service or application, or one of your applications or services. The following are examples of events:

- Amazon EC2 generates an event when the state of an instance changes from pending to running.
    
- Amazon EC2 Auto Scaling generates events when it launches or terminates instances.
    
- AWS CloudTrail publishes events when you make API calls.
    

You can also set up scheduled events that are generated on a periodic basis.

EventBridge is used to connect applications with a variety of data. It would not be able to detect updates to a DynamoDB table.