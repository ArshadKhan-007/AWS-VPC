# AWS VPC: Common Mistakes & Configuration Best Practices

Managing AWS VPCs can get tricky, especially for beginners. This document highlights **frequent mistakes** and **recommended configurations** to avoid downtime, misconfigurations, or security issues.

---

## Common Mistakes

1. **Overlapping CIDR blocks**
   - Causes VPC peering or Transit Gateway conflicts
   - Always plan CIDR ranges carefully

2. **Public access to private subnets**
   - Deploying resources in private subnets with public IPs or incorrect route tables
   - Use Bastion Hosts or NAT Gateways for secure access

3. **Misconfigured Security Groups & NACLs**
   - Overly permissive rules (0.0.0.0/0) → security risk
   - Conflicting rules causing blocked traffic

4. **Ignoring Route Table assignments**
   - Subnets not associated with the correct route table → traffic failures
   - Always verify route table links

5. **Not enabling VPC Flow Logs**
   - Difficult to debug traffic issues
   - Flow logs help track ACCEPT/REJECT traffic and security events

6. **Multiple unnecessary VPC peering connections**
   - Leads to complex mesh networks
   - Use Transit Gateway for multi-VPC architectures

7. **Skipping endpoint or private connectivity**
   - Accessing AWS services from private subnets without VPC Endpoints → unnecessary NAT traffic & costs

---

## Configuration Best Practices

- **Plan CIDR carefully** before creating VPCs
- **Use public/private subnet separation** for security
- **Leverage NACLs + Security Groups** for layered security
- **Enable VPC Flow Logs** for monitoring & troubleshooting
- **Use Transit Gateway** for multi-VPC setups instead of excessive peering
- **Use VPC Endpoints** for private AWS service access
- **Use Bastion Hosts or AWS Session Manager** for secure private instance access
- **Document all changes** in GitHub or internal documentation for team reference

---