# AWS VPC Peering

## What is VPC Peering?
VPC Peering allows **two VPCs to communicate privately** using private IP addresses.  

- Traffic never goes over the public internet  
- Useful for connecting multiple VPCs in the same or different AWS accounts/regions  
- Works with **route tables** to control traffic flow  

---

## Key Concepts
- **Non-transitive:** If VPC A peers with VPC B, and B peers with C, A cannot reach C automatically  
- **Overlapping CIDR ranges are not allowed**  
- Can peer **within the same AWS account** or **cross-account**  

---

## How VPC Peering Works
1. Create a **Peering Connection**  
2. Update **Route Tables** in both VPCs to allow traffic  
3. Use **Security Groups** to permit access to instances  

**Example:**  

- VPC-A CIDR: `10.0.0.0/16`  
- VPC-B CIDR: `10.1.0.0/16`  
- Peering allows EC2 in VPC-A to access RDS in VPC-B privately  

**Route Table Example (VPC-A):**

| Destination | Target             |
|------------|-------------------|
| 10.1.0.0/16 | VPC Peering Connection |

---

## Best Practices
- Use **non-overlapping CIDR blocks** for all peered VPCs  
- Use descriptive names for peering connections  
- Update **security groups** in addition to route tables  
- Monitor traffic with **VPC Flow Logs**  

---

## Real-World Analogy
Think of VPCs as **two gated communities**:  
- VPC Peering = private road connecting them  
- Only allowed vehicles (traffic) can pass  
- Each community still controls entry using their own gates (Security Groups)
