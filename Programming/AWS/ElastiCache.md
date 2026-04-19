Today’s web users don’t have a lot of patience. A 250-millisecond difference in response time between competing sites ultimately translates into a huge difference in user retention.

**ElastiCache is not a database in the traditional sense**, but rather a web service that provides managed in-memory caching for your applications. It is often used to improve the performance and scalability of applications by reducing the load on backend databases.

Amazon ElastiCache is **a fully managed in-memory data store and cache service**. The service improves the performance of web applications by retrieving information from managed in-memory caches, instead of relying entirely on slower disk-based databases.

**cache-as-a-service**

Has the ability to deploy, manage, and scale a distributed in-memory cache environment [in the cloud](https://www.cloudzero.com/blog/history-of-the-cloud).

Amazon ElastiCache relies on two different caching engines, Memcached and Redis.

### ElastiCache Memcached

Just like the name suggests, AWS ElastiCache for Memcached is meant to serve as an in-memory key-value cache or data store for Memcached assets. 

This is what you’ll turn to when you need the simplest caching model, or perhaps when looking to deploy large nodes with multiple cores and threads. 

### ElastiCache Redis

Amazon ElastiCache for Redis, on the other hand, is built on open-source Redis to run seamlessly with Redis clients — as a blazingly fast in-memory data store. It’s so quick, in fact, that it’s capable of sub-millisecond latency, in a bid to support demanding applications. 

You can, in particular, count on it to work with complex data types — like bitmaps, sorted sets, lists, sets, hashes, and strings. What’s more, it can power multiple databases, as well as maintain the persistence of your key store.

## Amazon ElastiCache Use Cases

- Updating and managing leaderboards in the gaming industry 
- Conducting real-time analytics while customers shop on e-commerce sites 
- Monitoring the status of customers’ accounts on subscription-based sites
- Processing and relaying messages on instant messaging platforms 
- Online media streaming 
- Performing geospatial processes
### Pros of Amazon ElastiCache

- **Fully-managed** – ElastiCache is a fully-managed [cloud-based solution](https://www.cloudzero.com/blog/cloud-service-providers). This means that while you enjoy the advanced caching capabilities, you don’t have to worry about backups, failure recovery, monitoring, configuration, setups, software patching, and hardware provisions. The service will take care of all that while, at the same time, consistently monitoring your clusters to keep your Redis operating efficiently. 
- **Improves application performance** – While a disk-based database would have your applications conducting slow roundtrips to retrieve information, ElastiCache provides in-memory data stores that substantially reduce the overall response times. The improvement is so huge that standard read or write operations end up taking less than a millisecond. This means you should be able to comfortably run demanding web applications that require quick real-time responses. 
- **Easily scalable** – Amazon ElastiCache allows you to begin small and then progressively scale up your capabilities as the application grows. You can, for instance, expand your Redis cluster environment to as much as 500 shard and 500 nodes, plus possibly even increase your cluster’s in-memory data up to 340TB. Then if you need to [reduce costs](https://www.cloudzero.com/blog/cloud-cost-management-tools/), you can conveniently scale down the resources without experiencing any form of downtime. 
- **Highly available** – Apart from running both cluster and non-cluster modes, AWS ElastiCache achieves high availability through automatic failover detection and mitigation. Primary node failures, for instance, are immediately resolved by standby replicas. The same applies to reading operations — if the primary one is busy, the read replicas swing into action to serve the data and keep your application running smoothly. 

### Cons of Amazon ElastiCache

- **Limited to Amazon-Hosted Services** – As an AWS service, ElastiCache doesn’t offer a lot of options when it comes to integration. You can only connect it to databases and applications that are hosted by Amazon. 

- **Learning curve** – Beginners on Amazon ElastiCache might need some time to learn the ropes. The user interface itself is not very intuitive, and its many options might feel a bit overwhelming when you’re getting started. 
- **Expensive** – Although AWS ElastiCache’s pricing system is pretty flexible and bills you only for what you use, the costs here can add up quickly over time. A decently sized company might find itself paying thousands of dollars per month after a year or so of continued use.
### AWS ElastiCache vs. Redis

Amazon ElastiCache, as we’ve established already, is all about setting up, running, and scaling an in-memory cache in the cloud. With its fast retrieval of data from managed in-memory caches, the service improves overall response times, and saves you the frustrations of relying entirely on slower disk-based databases. 

Redis, on the other hand, stands for Remote Dictionary Server — which is a swift, in-memory, open-source, BSD-licensed key-value data store. It’s typically leveraged as a queue, message broker, cache, and database. 

Now, that’s precisely where AWS ElastiCache for Redis comes in. It’s developed on open-source Redis to be compatible with Redis APIs, as well as operate seamlessly with Redis clients. In simple terms, you should be able to power your self-managed Redis applications and store data in open Redis format, all without reworking the code. 

### AWS ElastiCache vs. CloudFront

While AWS ElastiCache and AWS CloudFront are both caching solutions, their individual approaches and overall framework differ greatly. 

ElastiCache, for starters, enhances the performance of web applications by quickly retrieving information from fully-managed in-memory data stores. It utilizes Memcached and Redis, and manages to considerably reduce the time your applications would, otherwise, take to read data from disk-based databases. 

Amazon CloudFront seeks to boost the performance of web applications too. But, unlike ElastiCache, it acts as a [Content Delivery Network (CDN)](https://www.cloudflare.com/learning/cdn/what-is-a-cdn/) — which speeds up the delivery of web-based assets through endpoint caches that are positioned close to the traffic source. In other words, your web visitors load content from the closest caching server, instead of relying entirely on the original hosting server. 

### AWS ElastiCache vs. AWS DynamoDB

AWS DynamoDB is essentially a NoSQL database service that’s fully managed by Amazon. It holds its data items in Solid State Drives (SSDs), which are then cloned across three availability zones for increased reliability and availability. This saves administrators the trouble of building, maintaining, and scaling costly distributed database clusters. 

So, while DynamoDB can be classed in the “NoSQL Database-as-a-service” category, ElastiCache is Amazon’s specialized “Caching-as-a-Service” — as it offers fully-managed in-memory caches that work with Memcached and Redis.