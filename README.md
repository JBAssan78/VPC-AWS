# VPC-AWS Setup #

This will be a walk through ofr setting up a fully functional Virtual Private Cloud (VPC) in AWS, including the creation of public and private subnets, proper IP addressing, and network segmentation. You’ll learn how to configure route tables, internet gateways, and NAT gateways to ensure both secure private networking and controlled public access. By the end, you’ll understand each component’s purpose and how they work together to form a reliable, scalable cloud network foundation.

## VPC Overview ##

VPC CIDR: 10.10.0.0/16

This gives you 65,536 IP addresses, ranging from 10.10.0.0 to 10.10.255.255.

You can carve out many smaller subnets — in your case, /24 networks (each with 256 IPs).

| AZ         | Public Subnet | Private Subnet |
| ---------- | ------------- | -------------- |
| us-east-2a | 10.10.1.0/24  | 10.10.11.0/24  |
| us-east-2b | 10.10.2.0/24  | 10.10.12.0/24  |
| us-east-2c | 10.10.3.0/24  | 10.10.13.0/24  |

