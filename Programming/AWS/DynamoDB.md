Amazon DynamoDB is a serverless, NoSQL, fully managed database with single-digit millisecond performance at any scale.

DynamoDB delivers consistent single-digit millisecond performance for a shopping cart use case, whether you've 10 or 100 million users.
## DynamoDB use cases

Customers across all sizes, industries, and geographies use DynamoDB to build modern, serverless applications that can start small and scale globally. DynamoDB is ideal for use cases that require consistent performance at any scale with little to zero operational overhead. The following list presents some use cases where you can use DynamoDB:

- **Financial service applications** – Suppose you're a financial services company building applications, such as live trading and routing, loan management, token generation, and transaction ledgers. With DynamoDB [global tables](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/GlobalTables.html), your applications can respond to events and serve traffic from your chosen AWS Regions with fast, local read and write performance.
    
    DynamoDB is suitable for applications with the most stringent availability requirements. It removes the operational burden of manually scaling instances for increased storage or throughput, versioning, and licensing.
    
    You can use [DynamoDB transactions](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/transactions.html) to achieve atomicity, consistency, isolation, and durability (ACID) across one or more tables with a single request. [(ACID) transactions](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/transaction-apis.html) suit workloads that include processing financial transactions or fulfilling orders. DynamoDB instantly accommodates your workloads as they ramp up or down, enabling you to efficiently scale your database for market conditions, such as trading hours.
    
- **Gaming applications** – As a gaming company, you can use DynamoDB for all parts of game platforms, for example, game state, player data, session history, and leaderboards. Choose DynamoDB for its scale, consistent performance, and the ease of operations provided by its serverless architecture. DynamoDB is well suited for scale-out architectures needed to support successful games. It quickly scales your game’s throughput both in and out (scale to zero with no cold start). This scalability optimizes your architecture's efficiency whether you’re scaling out for peak traffic or scaling back when gameplay usage is low.
    
- **Streaming applications** – Media and entertainment companies use DynamoDB as a metadata index for content, content management service, or to serve near real-time sports statistics. They also use DynamoDB to run user watchlist and bookmarking services and process billions of daily customer events for generating recommendations. These customers benefit from DynamoDB's scalability, performance, and resiliency. DynamoDB scales to workload changes as they ramp up or down, enabling streaming media use cases that can support any levels of demand.
# Streams

A _DynamoDB stream_ is an ordered flow of information about changes to items in a DynamoDB table. When you enable a stream on a table, DynamoDB captures information about every modification to data items in the table.

Whenever an application creates, updates, or deletes items in the table, DynamoDB Streams writes a stream record with the primary key attributes of the items that were modified. A _stream record_ contains information about a data modification to a single item in a DynamoDB table. You can configure the stream so that the stream records capture additional information, such as the "before" and "after" images of modified items.

DynamoDB Streams helps ensure the following:

- Each stream record appears exactly once in the stream.
    
- For each item that is modified in a DynamoDB table, the stream records appear in the same sequence as the actual modifications to the item.
    

DynamoDB Streams writes stream records in near-real time so that you can build applications that consume these streams and take action based on the contents.

![[Pasted image 20250115132054.png]]

You can enable DynamoDB Streams on a table to create an event that invokes an AWS Lambda function.

If you enable DynamoDB Streams on a table, you can associate the stream Amazon Resource Name (ARN) with an Lambda function that you write. Immediately after an item in the table is modified, a new record appears in the table's stream. Lambda polls the stream and invokes your Lambda function synchronously when it detects new stream records.

A trigger cannot be enabled on a DynamoDB table. To create a trigger, a DynamoDB stream should be enabled on the specific DynamoDB table.

A DynamoDB stream cannot be used to create an Amazon SNS topic.