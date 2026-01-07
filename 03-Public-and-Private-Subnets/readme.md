# Public and Private Subnets in AWS VPC

## What is a Subnet?
A subnet is a segment of a VPC's IP address range.  
It helps organize resources, control traffic, and improve security.

---

## Public Subnet
- Has a route to the **Internet Gateway (IGW)**
- Hosts resources that need **public internet access** (e.g., web servers)
- Can be accessed directly from outside the VPC

**Example CIDR:** `10.0.1.0/24`  

---

## Private Subnet
- No direct route to the internet
- Hosts resources that should remain **internal** (e.g., databases, application servers)
- Outbound internet access only via **NAT Gateway**

**Example CIDR:** `10.0.2.0/24`  

---

## Why Separate Public and Private Subnets?
- **Security:** Keep sensitive resources private  
- **Traffic Control:** Public-facing vs internal resources  
- **Scalability:** Easier management of growth and services  
- **Blast Radius Control:** Problems in public subnet won’t affect private subnet

---

## Real-World Analogy
Think of a VPC as a gated society:
- Public subnet = shops & community areas accessible to everyone  
- Private subnet = residential homes with restricted access  

Only allowed traffic reaches each subnet.
