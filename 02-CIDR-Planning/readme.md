# CIDR Range Planning in AWS VPC

## What is CIDR?
CIDR (Classless Inter-Domain Routing) defines the IP address range for a VPC or subnet.  
It specifies:
- The starting IP address
- The size of the network

**Example:** `10.0.0.0/16`  
- `10.0.0.0` → starting address  
- `/16` → size of the network (number of IPs)

---

## Why CIDR Planning is Important
CIDR planning is **critical for designing scalable and secure VPCs**.

Key reasons:
- Determines how many resources (EC2, RDS, etc.) can be deployed
- Allows multiple subnets to be created within a VPC
- Supports future growth and scaling
- Prevents IP address exhaustion
- Required for VPC Peering, Transit Gateway, and hybrid connectivity

> ⚠️ Once a VPC is created, its CIDR cannot be easily changed.

---

## How CIDR is Used in a VPC
CIDR is applied at **two levels**:

1. **VPC level** – defines the total IP pool  
2. **Subnet level** – divides the VPC into smaller networks  

**Example:**
- VPC CIDR: `10.0.0.0/16` → total 65,536 IPs  
- Public Subnet: `10.0.1.0/24` → 256 IPs (usable: 251)  
- Private Subnet: `10.0.2.0/24` → 256 IPs  

> VPC CIDR = parent network  
> Subnets = child networks derived from parent

---

## Commonly Used CIDR Sizes
| CIDR | Total IPs | Use Case |
|------|-----------|----------|
| /16  | 65,536    | Large VPC (multi-subnet) |
| /20  | 4,096     | Medium VPC |
| /24  | 256       | Subnets (public/private) |

> AWS reserves 5 IPs per subnet for internal use.

---

## Best Practices
- Use **non-overlapping CIDR ranges** for multiple VPCs
- Plan CIDR based on **current + future needs**
- Keep separate ranges for **public and private subnets**
- Avoid very small CIDR blocks for production

---

## Common Mistakes to Avoid
- Overlapping CIDRs between VPCs (blocks VPC Peering)
- Too small CIDR blocks (limits scalability)
- Not reserving space for future subnets
- Forgetting AWS reserved IP addresses

---

## Real-World Analogy
Think of a VPC like a **city map**:
- VPC CIDR = city boundary  
- Subnets = neighborhoods inside the city  
- Choosing proper CIDR = ensuring every neighborhood has enough houses without overcrowding
