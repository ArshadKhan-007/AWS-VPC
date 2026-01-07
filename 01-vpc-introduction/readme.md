# AWS VPC Introduction

## What is a Virtual Private Cloud (VPC)?
A Virtual Private Cloud (VPC) is a logically isolated virtual network in AWS where you can launch resources in a secure and controlled environment.

It allows you to define:
- IP address range (CIDR)
- Subnets
- Routing rules
- Network security

---

## Why Do We Need a VPC?
A custom VPC is required for production workloads.

Key reasons:
- Network isolation
- Better security control
- Custom IP planning
- Separation of public and private resources

---

## How Does a VPC Work?
A VPC works by combining multiple networking components:
- CIDR defines the IP range
- Subnets divide the network
- Route tables control traffic flow
- Internet and NAT Gateways manage connectivity
- Security Groups and NACLs secure resources

---

## Real-Life Analogy
Think of a VPC as a gated society:
- CIDR block is the society land area
- Subnets are different buildings
- Route tables are internal roads
- Internet Gateway is the main gate
- Security Groups act as security guards

Only allowed traffic is permitted inside and outside the society.

---

## Key Points
- VPC is region-specific
- Supports public and private subnets
- Provides full network control
