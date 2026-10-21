# AWS Cloud Architecture Lab

## Project Overview

This beginner project documents the design of a secure, scalable web application architecture on Amazon Web Services (AWS).

## Project Goals

- Understand the core components of an AWS cloud environment.
- Design a Virtual Private Cloud (VPC) with public and private subnets.
- Plan how EC2 instances and Auto Scaling could support application availability.
- Document security considerations using IAM roles and security groups.
- Explore Amazon S3 for object storage and lifecycle management.

## Planned AWS Services

- Amazon VPC — network isolation and subnet design.
- Amazon EC2 — virtual servers for the application.
- EC2 Auto Scaling — adjusts the number of instances based on demand.
- IAM — identity and access management.
- Security Groups — control inbound and outbound traffic.
- Amazon S3 — object storage.

## Architecture Approach

The proposed design separates public-facing components from private application resources. Access is restricted according to the principle of least privilege. Availability, scalability, and cost are considered during the design.

## Project Status

Planning and documentation stage. AWS resources have not yet been deployed.

## What I Am Learning

- AWS networking fundamentals.
- Cloud security basics.
- Scalable architecture design.
- Technical documentation using GitHub.

## Disclaimer

This is a learning project. The architecture is a proposed design, not a production deployment.

## VPC Network Design

### Objective

Design a logically isolated AWS network for a web application, separating public-facing resources from application servers that should not be directly accessible from the public internet.

### Proposed IP Address Plan

| Component | IPv4 CIDR | Purpose |
|---|---|---|
| VPC | `10.0.0.0/16` | Main network address range |
| Public subnet | `10.0.1.0/24` | Hosts an internet-facing load balancer, if required |
| Private subnet | `10.0.2.0/24` | Hosts application EC2 instances |

The subnet ranges are within the VPC range and do not overlap.

### Planned Network Components

- **Internet Gateway:** Supports internet connectivity for resources with suitable routes and configuration.
- **Route tables:** Direct traffic to the appropriate destinations.
- **Public subnet:** Planned for the internet-facing load balancer.
- **Private subnet:** Planned for application servers without direct public internet access.
- **Security groups:** Restrict traffic to the required ports and sources.

### Security Considerations

- Do not allow unrestricted inbound access to application servers.
- Allow application traffic only from the appropriate load balancer or trusted sources.
- Follow the principle of least privilege.
- Review routing and security rules before deployment.

### Current Status

This is a proposed network design for learning purposes. The VPC, subnets, routes, and AWS resources have not been deployed.
