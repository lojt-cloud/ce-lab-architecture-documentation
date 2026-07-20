# Lab M2.08 - Architecture Documentation and Diagrams

**Repository:** [https://github.com/cloud-engineering-bootcamp/ce-lab-architecture-documentation](https://github.com/cloud-engineering-bootcamp/ce-lab-architecture-documentation)

**Activity Type:** Individual  
**Estimated Time:** 30-45 minutes

## Learning Objectives

- [ ] Create architecture diagrams
- [ ] Document system components
- [ ] Analyze cost implications
- [ ] Identify improvement opportunities
- [ ] Present architecture decisions

## Your Task

Document your Week 2 deployment comprehensively:
1. Create architecture diagram
2. Document all components
3. List security configurations
4. Calculate costs
5. Propose improvements

**Success:** Professional documentation ready for team review

## Required Documentation

### 1. Architecture Diagram

Create diagram showing:
- All EC2 instances
- Security groups
- Network flows
- Availability zones
- Load balancers (if used)

**Tools:**
- draw.io (diagrams.net)
- Lucidchart
- CloudCraft
- Or hand-drawn and scanned

### 2. Component Inventory

| Component | Type | Size | Purpose | Monthly Cost |
|-----------|------|------|---------|--------------|
| Web Server | EC2 | t3.small | Serve HTTP | $15 |
| Application | EC2 | t3.medium | Run Node.js | $30 |
| Security Groups | 4 SGs | N/A | Network security | Free |

### 3. Security Matrix

Document all security group rules with justification.

### 4. Cost Analysis

Current costs + optimization opportunities.

### 5. Improvement Plan

3 specific improvements you would make.

## 📤 What to Submit

**Submission Type:** GitHub Repository

Create a **public** GitHub repository named `ce-lab-architecture-docs` containing:
- `README.md` - Overview
- `ARCHITECTURE.md` - Detailed architecture
- `architecture-diagram.png` - Visual diagram
- `SECURITY.md` - Security documentation
- `COSTS.md` - Cost analysis
- `IMPROVEMENTS.md` - Proposed improvements

## Grading: 100 points
- Diagram quality: 25pts
- Documentation completeness: 25pts
- Cost analysis: 20pts
- Improvement proposals: 15pts
- Professional presentation: 15pts
