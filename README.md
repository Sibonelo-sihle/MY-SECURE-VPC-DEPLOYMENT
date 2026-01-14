# Secure AWS VPC Infrastructure Deployment

## Project Objective
The goal of this project was to design and implement a Virtual Private Cloud (VPC) supporting a secure, tiered architecture. The design ensures that resources in a private subnet can access the internet for updates via a NAT Gateway, while remaining protected from direct inbound public traffic.

## Architecture Diagram

COMING SOON

## Technical Specifications
- **VPC CIDR:** 10.0.0.0/16
- **Public Subnet:** 10.0.25.0/24 (Same AZ as Private Subnet)
- **Private Subnet:** 10.0.50.0/24 (Same AZ as Public Subnet)
- **Gateways:** Internet Gateway (IGW) for public access; NAT Gateway for private outbound traffic.
- **Security:** Network ACL (NACL) applied to both subnets for traffic control.

## Connectivity Verification
To verify the infrastructure:
1. I confirmed the **Public Route Table** points to the **Internet Gateway** (0.0.0.0/0 -> igw-id).
2. I confirmed the **Private Route Table** points to the **NAT Gateway** (0.0.0.0/0 -> nat-id).
3. **Test:** By launching an EC2 instance in the Private Subnet, I can run `ping google.com`. The traffic travels through the NAT Gateway. External users cannot SSH directly into this instance, ensuring security.

## Infrastructure Proof
- [ ] VPC CIDR configured correctly.
- [ ] NAT and IGW status: Available/Attached.
- [ ] Route Table associations verified.
