# Cost Analysis

## Current Month Estimate

| Component | Type | Size | Purpose | Monthly Cost (24/7) |
|-----------|------|------|---------|----------------------|
| Bastion instance | EC2 | t3.micro | SSH gateway | ~$7.60 |
| Web instance | EC2 | t3.micro | Nginx proxy, public | ~$7.60 |
| App instance | EC2 | t3.micro | Node.js app | ~$7.60 |
| Database instance | EC2 | t3.micro | Simulated MySQL | ~$7.60 |
| Security Groups | 4 SGs | N/A | Network security | Free |
| SNS Topic | ec2-alerts | N/A | Alarm notifications | Free (low volume) |
| CloudWatch Alarms | 2 alarms | N/A | CPU + status monitoring | ~$0.20 |
| S3 Bucket (IAM lab) | N/A | N/A | Test bucket, minimal data | ~$0.02 |

| **Total (if all ran 24/7)** | | | | **~$30.62/month** |

## 24/7 vs. Start-Stop

Running all four EC2 instances continuously costs roughly $30/month for
compute alone. Stopping instances when not actively in use can save up to
70% of compute costs, since EC2 billing is per-hour while running. However,
this only makes sense for non-customer-facing tiers (bastion, app, database
during development/testing). The web tier, if genuinely serving live
customer traffic, needs to stay running continuously, since downtime
directly costs customer trust and potential lost business.

## On-Demand vs. Reserved

Reserved Instances become cost-effective once traffic is stable and
predictable, offering discounts of roughly 40-60% in exchange for a 1-3
year commitment. For a new or unpredictable workload (like this
lab environment), On-Demand is the right choice. Committing to Reserved
pricing before understanding real usage patterns risks paying for capacity
that's over or under-provisioned relative to actual need.

## Biggest Cost Driver

All four instances are currently the same size (t3.micro), so compute is
evenly split rather than one component dominating. In a real production
version of this architecture, the app tier would likely become the biggest
driver, since application logic typically needs more CPU/memory than a
simple reverse proxy (web) or a lightweight bastion. This lab's simulated
services don't reflect that yet, since everything is deliberately minimal
for learning purposes.