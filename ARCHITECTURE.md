# Architecture Documentation and Diagrams - Solution

**Student Name:** Balint Lojt
**Date Completed:20/07/2026
## RENAME this file TO ARCHITECTURE.md!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
---

## Overview

This lab documents the architecture built across Week 2 labs, including
the multi-tier security group setup (bastion, web, app, database), the
Node.js deployment (PM2 + Nginx), IAM roles for EC2, and CloudWatch
monitoring.

---

## 1. Architecture Diagram

**Tool used:** draw.io 

**File:** `architecture-diagram.png`

**Diagram should show:**
- [ ] All EC2 instances (bastion, web, app, database)
- [ ] Security groups and their relationships
- [ ] Network flow arrows (internet → web → app → database)
- [ ] Availability zone(s)
- [ ] Public vs. private subnet placement
- [ ] SSH access path (bastion only)

---

## 2. Component Inventory


|
 Component 
|
 Type 
|
 Size 
|
 Purpose 
|
 Monthly Cost (est.) 
|
|
-----------
|
------
|
------
|
---------
|
----------------------
|
|
 Bastion instance 
|
 EC2 
|
 t3.micro 
|
 SSH entry point 
|
 $___ 
|
|
 Web instance 
|
 EC2 
|
 t3.micro 
|
 Nginx reverse proxy, public HTTP 
|
 $___ 
|
|
 App instance 
|
 EC2 
|
 t3.micro 
|
 Node.js application 
|
 $___ 
|
|
 Database instance 
|
 EC2 
|
 t3.micro 
|
 Simulated DB (nc listener) 
|
 $___ 
|
|
 Security Groups 
|
 4+ SGs 
|
 N/A 
|
 Network access control 
|
 Free 
|
|
 SNS Topic 
|
 ec2-alerts 
|
 N/A 
|
 Alarm notifications 
|
 Free (low volume) 
|
|
 CloudWatch Alarms 
|
 2 alarms 
|
 N/A 
|
 CPU + status monitoring 
|
 $___ 
|
|
 S3 Bucket 
|
 ce-bootcamp-m2-05 
|
 N/A 
|
 IAM role test bucket 
|
 $___ 
|

---

## 3. Security Matrix

**File:** `SECURITY.md`

Every detail of the security matrix can be found in the SECURITY.md file where I explain all the connections (in and outbound) amond with the reasoning why I built it this way. 


---

## 4. Cost Analysis

**File:** `COSTS.md`

- Current monthly cost estimate (all running resources)
- Cost if everything ran 24/7 vs. stopped when not in use
- Comparison: on-demand vs. reserved (tie back to Cost Estimation lab)
- Biggest cost driver, and why

---

## 5. Improvement Plan

**File:** `IMPROVEMENTS.md`

Propose 3 specific, concrete improvements. Good candidates based on this
week's actual gaps:
1. NAT Gateway for private subnets (app/database currently need temporary
   public IPs to reach the internet - a real architectural gap identified
   during the multi-tier lab)
2. [Auto Scaling / Load Balancer for the web tier]
3. [Something cost-related, e.g. Reserved Instances once traffic is predictable]

---

## Files Checklist

- [ ] `README.md` - Overview
- [ ] `ARCHITECTURE.md` - Detailed architecture description
- [ ] `architecture-diagram.png` - Visual diagram
- [ ] `SECURITY.md` - Security documentation
- [ ] `COSTS.md` - Cost analysis
- [ ] `IMPROVEMENTS.md` - Proposed improvements
