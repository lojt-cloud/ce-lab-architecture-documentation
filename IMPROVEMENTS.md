# Improvement Plan

## 1. NAT Gateway for private subnets

Currently, the app and database instances have no public IP by design
(for security), but this means they have no route to the internet at all
for tasks like installing packages. During this week's labs, this was
worked around with temporary Elastic IPs. It is a real compromise, since it
briefly exposes these instances to the public internet even though
security groups still restrict inbound access. A proper NAT Gateway would
let private instances reach the internet outbound-only, with zero inbound
exposure, closing this gap permanently.

## 2. Auto Scaling and Load Balancer for the web tier

Right now there's a single web instance. If it fails or gets overwhelmed
by traffic, the whole customer-facing service goes down. Adding an Auto
Scaling Group with an Application Load Balancer in front of it would
distribute traffic across multiple instances, automatically replace a
failed instance, and scale capacity up or down based on real demand,
rather than relying on one fixed-size server.

## 3. Reserved Instances once traffic is predictable

All four instances currently run On-Demand, which is the right choice
while usage patterns are still unknown, but costs more per hour long-term.
Once real traffic data shows consistent, predictable usage, switching to
Reserved Instances (or Savings Plans) could cut compute costs by 40-60%
without any change to performance or architecture. Purely a pricing
optimization once the workload is well understood.