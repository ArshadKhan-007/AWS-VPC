# Internet Gateway (IGW) in AWS VPC

## What is an Internet Gateway?
An Internet Gateway (IGW) is a horizontally scaled, redundant AWS component that allows **communication between your VPC and the Internet**.

- Acts as a bridge between VPC and public networks
- Enables public-facing resources to send/receive traffic
- Associated at the **VPC level**, not per subnet

---

## Key Concepts
- Only **one IGW per VPC**  
- Needed for **public subnet** connectivity  
- Works with **route tables** to control traffic flow  
- Fully managed by AWS → no servers to maintain  

---

## How IGW Works
- Traffic from public subnet → route table → IGW → Internet  
- Incoming traffic is allowed only if **security groups allow it**  
- Outbound traffic follows the same path in reverse  

**Example Route Table for Public Subnet:**
| Destination | Target |
|------------|--------|
| 0.0.0.0/0  | IGW    |
| 10.0.0.0/16 | local  |

---

## Best Practices
- Attach IGW only to VPCs that need **public internet access**  
- Use descriptive names (e.g., `my-vpc-igw`)  
- Combine with **security groups** to protect instances  
- Avoid exposing sensitive resources directly to the internet  

---

## Real-World Analogy
Think of IGW as the **main gate of a gated society**:  
- Public subnet = shops & community areas  
- IGW = main gate allowing people in/out  
- Security groups = security guards checking who can enter/exit
