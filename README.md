# AWS Application Load Balancer – Path Based Routing with HTTPS

## 🏗️ Architecture Diagram

![Architecture Diagram](aws-alb-path-based-routing/ALB architecture.png)


## Overview
This project demonstrates how to build a scalable and secure web architecture using an **Application Load Balancer (ALB)** with **path-based routing**, **multiple target groups**, **HTTPS using ACM**, and **Route 53 DNS routing**.

---

## Architecture Highlights
- Internet-facing ALB
- Private EC2 instances across multiple AZs
- Path-based routing (/movies, /shows)
- HTTP to HTTPS redirection
- Multiple target groups
- Route 53 Alias record

---

## EC2 Setup
- 3 EC2 instances launched in private subnets
- Nginx installed using user data scripts
- Each instance serves different content

---

**Traffic Flow**

User → Route 53 (www.cloudkarna.in)
     → Application Load Balancer (HTTPS :443)
       ├── /        → Homepage Target Group
       ├── /movies/ → Movies Target Group
       └── /shows/  → Shows Target Group
## Target groups

Target Group	Path	Health Check	Instances
Homepage	/	/homepage/	Subnet 1A
Movies	/movies/*	/movies/	Subnet 1B
Shows	/shows/*	/shows/	Subnet 1C


---

## Load Balancer Configuration
- Listener 80 → Redirect to 443
- Listener 443 → SSL termination using ACM
- Routing rules forward traffic to appropriate target groups

---

## DNS
- Route 53 Alias A record pointing to ALB
- Domain secured with HTTPS

---

## Outcome
- Secure, scalable architecture
- Clean separation of services
- Production-like ALB configuration

---


Designed an ALB-based architecture with HTTPS and path-based routing to multiple backend services using target groups, Route 53, and ACM.


