Amazon Resource Names (ARNs) uniquely identify AWS resources. We require an ARN when you need to specify a resource unambiguously across all of AWS, such as in IAM policies, Amazon Relational Database Service (Amazon RDS) tags, and API calls.

### Examples

IAM user
```
arn:aws:iam::`123456789012`:user/`johndoe`
```

SNS topic
```
arn:aws:sns:`us-east-1`:`123456789012`:`example-sns-topic-name`
```

VPC
```
arn:aws:ec2:`us-east-1`:`123456789012`:vpc/`vpc-0e9801d129EXAMPLE`
```
## ARN format

The following are the general formats for ARNs. The specific formats depend on the resource. To use an ARN, replace the `italicized` text with the resource-specific information. Be aware that the ARNs for some resources omit the Region, the account ID, or both the Region and the account ID.

`` arn:`partition`:`service`:`region`:`account-id`:`resource-id` arn:`partition`:`service`:`region`:`account-id`:`resource-type`/`resource-id` arn:`partition`:`service`:`region`:`account-id`:`resource-type`:`resource-id` ``

`partition`

The partition in which the resource is located. A _partition_ is a group of AWS Regions. Each AWS account is scoped to one partition.

The following are the supported partitions:

- `aws` - AWS Regions
    
- `aws-cn` - China Regions
    
- `aws-us-gov` - AWS GovCloud (US) Regions
    

`service`

The service namespace that identifies the AWS product.

`region`

The Region code. For example, `us-east-2` for US East (Ohio). For the list of Region codes, see [Regional endpoints](https://docs.aws.amazon.com/general/latest/gr/rande.html#regional-endpoints) in the _AWS General Reference_.

`account-id`

The ID of the AWS account that owns the resource, without the hyphens. For example, `123456789012`.

`resource-type`

The resource type. For example, `vpc` for a virtual private cloud (VPC).

`resource-id`

The resource identifier. This is the name of the resource, the ID of the resource, or a [resource path](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference-arns.html#arns-paths). Some resource identifiers include a parent resource (sub-resource-type/parent-resource/sub-resource) or a qualifier such as a version (resource-type:resource-name:qualifier).