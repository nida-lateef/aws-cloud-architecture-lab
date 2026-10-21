# AWS Cloud Architecture Lab

## Project Overview

This beginner project documents the design of a secure, scalable web application architecture on Amazon Web Services (AWS).

## Project Goals

- Understand the core components of an AWS cloud environment.
- Design a Virtual Private Cloud (VPC) with public and private subnets.
- Plan how EC2 instances and Auto Scaling could support application availability.
- Document security considerations using IAM roles and security groups.
- Explore Amazon S3 for object storage and lifecycle management.

  ## Hands-on Labs

### Lab 1: Amazon S3 Bucket Basics
- Created an S3 general-purpose bucket in the Sydney region.
- Practised uploading and deleting an object.
- Verified that Block Public Access was enabled.

[View Lab 1: S3 Bucket Basics](labs/s3-bucket-basics.md)


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

## Routing and NAT Gateway

### Route Table Design

Route tables determine where network traffic is directed.

- **Public subnet route table:** Includes a default IPv4 route (`0.0.0.0/0`) to the Internet Gateway for internet-bound traffic.
- **Private subnet route table:** Includes a default IPv4 route (`0.0.0.0/0`) to a NAT Gateway for outbound internet access, if required.
- **Local route:** Allows communication within the VPC's IPv4 network range.

### NAT Gateway Purpose

A NAT Gateway in a public subnet can allow resources in a private subnet to initiate outbound IPv4 connections to the internet without requiring those resources to have public IPv4 addresses.

### Security Notes

- Private application servers should not be directly exposed to the public internet.
- Security groups should allow only the traffic required by the application.
- The NAT Gateway needs a suitable route to an Internet Gateway, and the private subnet needs a route to the NAT Gateway.
- NAT Gateway usage can incur AWS charges, so costs must be considered before deployment.

### Current Status

This routing plan is conceptual and has not been deployed in AWS.

## Security Group Design

### Purpose

Security groups act as virtual firewalls for AWS resources. They control allowed inbound and outbound traffic.

### Proposed Rules

| Resource | Direction | Protocol / Port | Source | Purpose |
|---|---|---|---|---|
| Load balancer | Inbound | HTTPS / TCP 443 | Intended client sources, such as `0.0.0.0/0` for a public website | Allow secure web requests |
| Application EC2 | Inbound | Application port, e.g. TCP 8080 | Load balancer security group | Allow application traffic from the load balancer |
| Application EC2 | Inbound | SSH / TCP 22 | Not open to the public internet | Avoid unrestricted administrative access |

### Security Principles

- Allow only the traffic required by the application.
- Reference the load balancer security group as the source for application traffic where appropriate.
- Review outbound rules and restrict them when the application requirements permit.
- Apply least privilege and review security group rules regularly.

### Current Status

These are proposed example rules for learning purposes. They have not been configured or tested in a live AWS environment.


## Architecture Diagram

![AWS VPC Web Architecture Diagram](./AWS%20VPC%20Web%20Architecture%20Diagram.png)

This diagram illustrates the proposed VPC network, public and private subnets, load balancer, NAT Gateway, EC2 instances, and Amazon S3. It is a conceptual design and has not been deployed in AWS.

## Object Retrieval Test

- Downloaded the test object from the S3 bucket.
- Confirmed that the download completed successfully.
- Practised the basic S3 object workflow: upload, download, and delete.

## Lab Outcome

Successfully practised basic S3 bucket and object management, inspected default encryption, and verified that public access was blocked.

