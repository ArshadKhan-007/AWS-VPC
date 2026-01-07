# AWS Route Tables

## What is a Route Table?
A Route Table defines how traffic flows **within a VPC** and **between subnets**.

- Determines which path network traffic takes
- Controls communication between subnets
- Can be associated with one or more subnets

---

## Key Concepts
- Each subnet **must be associated** with a route table
- Default route tables exist in every VPC
- You can create **custom route tables** for different subnet groups
- Routes define:
  - **Destination:** where traffic is going
  - **Target:** where traffic should be sent

---

## Example
- Public subnet route table might have routes for internal VPC subnets  
- Private subnet route table can restrict traffic within the VPC  

| Destination | Target        |
|------------|---------------|
| 10.0.1.0/24 | local        |
| 10.0.2.0/24 | local        |

> Routes can be customized to control traffic flow across subnets.

---

## Best Practices
- Use descriptive names for route tables (e.g., `public-rt`, `private-rt`)  
- Keep separate route tables for different subnet types  
- Avoid overlapping routes to prevent misrouting  
- Always associate every subnet with a route table

---

## Real-World Analogy
Think of route tables as **street maps within a gated society**:
- Each subnet = a neighborhood  
- Routes = streets connecting neighborhoods  
- Traffic follows these streets to reach its destination
