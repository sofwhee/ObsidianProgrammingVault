**Glacier is:**

- Long term archive storage
- Extremely cheap to store
- Potentially very expensive to retrieve
- Takes up to 4 hours to "read back" your data (so only store items you know you won't need to retrieve for a long time)

As it got mentioned in JDL's comment, there are several interesting aspects in terms of pricing. For example Glacier, S3, EFS allocates the storage for you based on your usage, while at EBS you need to predefine the allocated storage. Which means, you need to over estimate. ( However it's easy to add more storage to your EBS volumes, it requires some engineering, which means you always "overpay" your EBS storage, which makes it even more expensive.)