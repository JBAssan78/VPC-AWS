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

# Subnet Breakdown #

You divided the VPC into /24 subnets, which is typical for separating public and private resources.

Each /24 subnet provides 256 IP addresses (251 usable).

A clean structure would look like this:

Public Subnets (Example)

10.10.1.0/24

10.10.2.0/24

10.10.3.0/24
These are typically used for:

Load balancers

Bastion hosts

NAT Gateway

Any resource needing direct Internet access

Private Subnets (Example)

10.10.11.0/24

10.10.12.0/24

10.10.13.0/24
These are used for:

EC2 application servers

Databases (RDS)

Internal services
These subnets do not have direct Internet access — they rely on a NAT Gateway in a public subnet for outbound traffic.

## Availability Zones (AZ) – us-east-2 ##

The region US-East-2 has three AZs:

us-east-2a

us-east-2b

us-east-2c

A typical high-availability layout would be:

AZ	Public Subnet	Private Subnet
us-east-2a	10.10.1.0/24	10.10.11.0/24
us-east-2b	10.10.2.0/24	10.10.12.0/24
us-east-2c	10.10.3.0/24	10.10.13.0/24

This creates redundant networking across all 3 AZs and supports:

Multi-AZ load balancing

Multi-AZ database deployments

Highly available application infrastructure

## Create VPC ##

![image_alt](https://github.com/JBAssan78/VPC-AWS/blob/48ba46fdd8c780a837f6cda0fa84941cc93afdb8/Screenshot%202025-11-11%20184708.png)


