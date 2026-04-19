**EFS is:**

- [Generally Available](https://aws.amazon.com/about-aws/whats-new/2016/06/amazon-elastic-file-system-efs-is-now-generally-available/) (out of preview), but may not yet be available in your region
- Network filesystem (that means it may have bigger latency but it can be shared across several instances; even between regions)
- It is expensive compared to EBS (~10x more) but it gives extra features.
- It's a highly available service.
- It's a managed service
- You can attach the EFS storage to an EC2 Instance
- Can be accessed by multiple EC2 instances simultaneously
- Since 2016.dec.20 it's possible to attach your EFS storage directly to [on-premise servers via Direct Connect.](https://aws.amazon.com/blogs/aws/amazon-efs-update-on-premises-access-via-direct-connect-vpc/) ()