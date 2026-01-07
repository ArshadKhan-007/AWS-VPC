# AWS Transit Gateway

## What is a Transit Gateway?
AWS Transit Gateway (TGW) is a **hub that connects multiple VPCs and on-premises networks** through a single gateway.  

- Simplifies network architecture  
- Eliminates the need for **multiple VPC peering connections**  
- Enables **centralized routing** between VPCs, VPNs, and Direct Connect  

---

## Key Concepts
- Acts as a **central hub**  
- VPCs are **spokes** connected to the hub  
- Supports **cross-account and cross-region connections**  
- Works with **route tables** to control traffic between attachments  

---

## How Transit Gateway Works
1. Create a **Transit Gateway**  
2. Attach multiple **VPCs or VPNs** to the TGW  
3. Configure **TGW route tables** for routing traffic between attachments  

**Example:**
- VPC-A CIDR: `10.0.0.0/16`  
- VPC-B CIDR: `10.1.0.0/16`  
- VPC-C CIDR: `10.2.0.0/16`  
- Transit Gateway connects all three VPCs → traffic flows centrally without multiple peering links  

---

## Best Practices
- Use TGW for **multi-VPC architecture** to reduce complexity  
- Organize **route tables per hub-spoke architecture**  
- Monitor traffic using **VPC Flow Logs**  
- Combine with **security groups and NACLs** for layered security  

---