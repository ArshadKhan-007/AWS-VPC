# AWS VPC Endpoints

## What is a VPC Endpoint?
A VPC Endpoint allows **private connectivity** between your VPC and supported AWS services **without using the public internet**.  

- Traffic stays within AWS network  
- Increases security and reduces latency  
- No need for NAT Gateway or Internet Gateway for service access  

---

## Types of VPC Endpoints
1. **Interface Endpoint**  
   - Uses **Elastic Network Interface (ENI)** in your subnet  
   - Supports services like **EC2 API, S3 (via private link)**  
   - Provides private IP access to AWS services  

2. **Gateway Endpoint**  
   - Only for **S3 and DynamoDB**  
   - Route traffic directly from subnet to service  
   - Added in **route tables**  

---

## How VPC Endpoint Works
- Traffic destined for the service is routed **via the endpoint**  
- Route table is updated (for Gateway endpoints)  
- Security Groups control access (for Interface endpoints)  

**Example:**  

- VPC CIDR: `10.0.0.0/16`  
- Private Subnet: `10.0.2.0/24`  
- Gateway Endpoint: S3 → add route `Destination: S3 Prefix / Target: vpce-xxxxxx`  
- Now EC2 in private subnet can access S3 **without Internet Gateway**  

---

## Best Practices
- Use **Gateway Endpoints** for S3 and DynamoDB to save NAT Gateway costs  
- Use **Interface Endpoints** for other AWS services  
- Restrict access using **VPC endpoint policies**  
- Combine with **Security Groups** for granular control  

---

## Real-World Analogy
Think of a VPC Endpoint as a **private tunnel to a warehouse**:  
- EC2 = delivery trucks inside VPC  
- Tunnel = endpoint connecting directly to S3  
- No need to go through public roads (internet) → safe & fast
