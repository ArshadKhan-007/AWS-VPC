# AWS Network ACLs (NACLs)

## What is a Network ACL?
A Network ACL (Access Control List) is a **subnet-level firewall** in AWS VPC that controls **inbound and outbound traffic**.

- Applies to **all resources in a subnet**
- Provides an additional security layer beyond Security Groups
- Allows **Allow** and **Deny** rules
- Stateless: responses must be explicitly allowed

---

## Key Concepts
- Each subnet can be associated with **one NACL at a time**  
- NACL contains **ordered rules** with numbers (lower number = higher priority)  
- Rules can **allow** or **deny** traffic based on:  
  - Protocol (TCP/UDP/ICMP)  
  - Port range  
  - Source/Destination IP

---

## Rule Number Explained
- **Rule Number** decides the priority/order of evaluation  
- AWS evaluates rules **top-down** (lowest number first)  
- First matching rule is applied  
- If no match → default action applies (Allow/Deny depending on default NACL)

**Example:**

| Rule # | Type       | Protocol | Source        | Action |
|--------|-----------|---------|--------------|--------|
| 100    | All Traffic | All     | 203.0.113.0/24 | DENY   |
| 110    | HTTP       | TCP/80 | 0.0.0.0/0     | ALLOW  |
| 120    | HTTPS      | TCP/443 | 0.0.0.0/0     | ALLOW  |

**Traffic scenarios:**  
- Incoming traffic from `203.0.113.5` → matches **Rule 100** → DENY  
- Incoming traffic to port 80 from any other IP → matches **Rule 110** → ALLOW  

**Pro Tips:**  
- Leave spaces between rule numbers (e.g., 100, 110, 120) → easy future insertion  
- Avoid duplicate rule numbers → can cause confusion  
- Always review **top-down order** → misconfigured rules can block traffic

---

## Default vs Custom NACL
| Type         | Inbound | Outbound |
|--------------|---------|---------|
| Default NACL | Allow all | Allow all |
| Custom NACL  | Deny all by default | Deny all by default |

> Custom NACLs are used for stricter or specific traffic rules.

---

## Example
**Scenario:** Block traffic from a specific IP range  
- Subnet: `10.0.2.0/24`  
- Rule:  
  - Rule number: 100  
  - Type: All Traffic  
  - Protocol: All  
  - Source: `203.0.113.0/24`  
  - Action: DENY  

---

## Best Practices
- Use NACLs for **broad subnet-level rules**  
- Use Security Groups for **instance-level fine-grained control**  
- Avoid overly complex rules  
- Always test NACL rules in a staging environment first  

---

## Real-World Analogy
Think of NACL as a **security gate at the entrance of a neighborhood**:
- Subnet = neighborhood  
- NACL = gate controlling who can enter/leave  
- Security Groups = house-level locks for individual homes
