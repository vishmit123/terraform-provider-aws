---
subcategory: "VPC"
layout: "aws"
page_title: "AWS: aws_vpc"
description: |-
  Provides a VPC resource.
---

# Resource: aws_vpc

Provides a VPC resource.

## Example Usage

Basic usage:

```terraform
resource "aws_vpc" "main" {
  cidr_block = "10.0.0.0/16"
}
```

Basic usage with tags:

```terraform
resource "aws_vpc" "main" {
  cidr_block       = "10.0.0.0/16"
  instance_tenancy = "default"

  tags = {
    Name = "main"
  }
}
```

## Argument Reference

The following arguments are supported:

* `cidr_block` - (Required) The CIDR block for the VPC.
* `instance_tenancy` - (Optional) A tenancy option for instances launched into the VPC. Default is `default`, which
  makes your instances shared on the host. Using either of the other options (`dedicated` or `host`) costs at least $2/hr.
* `enable_dns_support` - (Optional) A boolean flag to enable/disable DNS support in the VPC. Defaults true.
* `enable_dns_hostnames` - (Optional) A boolean flag to enable/disable DNS hostnames in the VPC. Defaults false.
* `enable_classiclink` - (Optional) A boolean flag to enable/disable ClassicLink
  for the VPC. Only valid in regions and accounts that support EC2 Classic.
  See the [ClassicLink documentation][1] for more information. Defaults false.
* `enable_classiclink_dns_support` - (Optional) A boolean flag to enable/disable ClassicLink DNS Support for the VPC.
  Only valid in regions and accounts that support EC2 Classic.
* `assign_generated_ipv6_cidr_block` - (Optional) Requests an Amazon-provided IPv6 CIDR
block with a /56 prefix length for the VPC. You cannot specify the range of IP addresses, or
the size of the CIDR block. Default is `false`.
* `tags` - (Optional) A map of tags to assign to the resource.

## Attributes Reference

In addition to all arguments above, the following attributes are exported:

* `arn` - Amazon Resource Name (ARN) of VPC
* `id` - The ID of the VPC
* `cidr_block` - The CIDR block of the VPC
* `instance_tenancy` - Tenancy of instances spin up within VPC.
* `enable_dns_support` - Whether or not the VPC has DNS support
* `enable_dns_hostnames` - Whether or not the VPC has DNS hostname support
* `enable_classiclink` - Whether or not the VPC has Classiclink enabled
* `main_route_table_id` - The ID of the main route table associated with
     this VPC. Note that you can change a VPC's main route table by using an
     [`aws_main_route_table_association`](/docs/providers/aws/r/main_route_table_association.html).
* `default_network_acl_id` - The ID of the network ACL created by default on VPC creation
* `default_security_group_id` - The ID of the security group created by default on VPC creation
* `default_route_table_id` - The ID of the route table created by default on VPC creation
* `ipv6_association_id` - The association ID for the IPv6 CIDR block.
* `ipv6_cidr_block` - The IPv6 CIDR block.
* `owner_id` - The ID of the AWS account that owns the VPC.


[1]: https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/vpc-classiclink.html

## Import

VPCs can be imported using the `vpc id`, e.g.

```
$ terraform import aws_vpc.test_vpc vpc-a01106c2
```
