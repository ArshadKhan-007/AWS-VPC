# AWS Bastion Host

## What is a Bastion Host?
A Bastion Host is a **special-purpose server** used to **securely access instances in private subnets**.  

- Acts as a **jump server**  
- Only instance that has public access  
- Provides **SSH/RDP access** to private resources  

---

## Key Concepts
- Deployed in a **public subnet**  
- Security Groups restrict access to **specific IP addresses**  
- All private instances remain **non-public**  
- Logs can be monitored for **audit & security**  

---

## How Bastion Host Works
1. User connects via SSH/RDP to Bastion Host (public IP)  
2. Bastion Host connects to private instances using private IPs  
3. No private instance is exposed to the internet  

**Example:**  
- VPC CIDR: `10.0.0.0/16`  
- Public Subnet: `10.0.1.0/24` → Bastion Host  
- Private Subnet: `10.0.2.0/24` → EC2 (private)  
- User SSH: `ssh -i key.pem ec2-user@bastion-public-ip` → then access private EC2  

---

## Best Practices
- Restrict Bastion access to **trusted IPs** only  
- Enable **logging** and **audit trails**  
- Use **key-based authentication** instead of passwords  
- Consider **session manager** (AWS Systems Manager) as alternative  

---

## Real-World Analogy
Think of a Bastion Host as a **guarded gateway to a private office**:  
- Only authorized personnel (users) can enter  
- Private rooms (EC2 in private subnet) remain inaccessible directly from the outside  
- Logs = security cameras recording access
