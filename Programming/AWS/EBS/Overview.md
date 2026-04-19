**EBS is:**

- A block storage (so you need to format it). This means you are able to choose which type of file system you want.
- As it's a block storage, you can use Raid 1 (or 0 or 10) with multiple block storages
- It is really fast
- It is relatively cheap
- With the new announcements from Amazon, you can store up to 16TB data per storage on SSD-s.
- You can snapshot an EBS (while it's still running) for backup reasons
- But it only exists in a particular region. Although you can migrate it to another region, you cannot just access it across regions (only if you share it via the EC2; but that means you have a file server)
- You need an EC2 instance to attach it to
- [New feature](https://aws.amazon.com/blogs/aws/amazon-ebs-update-new-elastic-volumes-change-everything/) (2017.Feb.15): You can now increase volume size, adjust performance, or change the volume type while the volume is in use. You can continue to use your application while the change takes effect.