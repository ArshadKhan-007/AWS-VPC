# AWS VPC Flow Logs

## What are VPC Flow Logs?
VPC Flow Logs capture **IP traffic going in and out of network interfaces** in your VPC.  

- Helps **monitor, audit, and troubleshoot network traffic**  
- Can capture traffic for **VPC, subnet, or individual ENIs**  
- Stored in **CloudWatch Logs** or **S3**  

---

## Key Concepts
- **Resource types:** VPC, Subnet, Network Interface  
- **Traffic types:** ACCEPT / REJECT  
- **Log format:** source IP, destination IP, ports, protocol, action, bytes transferred  
- **Destination options:** CloudWatch Logs or S3 for analysis  

---

## How VPC Flow Logs Work
1. Enable flow logs on a VPC, subnet, or ENI  
2. Choose **IAM role** to write logs  
3. Logs capture **all allowed and rejected traffic**  
4. Analyze logs to identify traffic patterns, security issues, or connectivity problems  

**Example Use Case:**  
- VPC CIDR: `10.0.0.0/16`  
- Subnet: `10.0.2.0/24` (private)  
- Flow logs show that traffic from IP `203.0.113.10` was **REJECTED** by NACL rule 100  

---