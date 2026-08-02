The system and user pool configurations
  
Why system workloads are isolated
  System workloads are isolated so if application components go down, the infrastructure components can still run.
Autoscaling minimums and maximums
  System pool: min 2, max 4
  User pool: min 2, max 100
Labels and taints
  Autoscaling: true
  Count: 2
  Image: AKSUbuntu-2404gen2containerd-202607.20.0
  Labels:
    workload: system
  Max: 4
  Min: 2
  Mode: System
  Name: agentpool
  State: Succeeded
  Taints:
  - CriticalAddonsOnly=true:NoSchedule
- Autoscaling: true
  Count: 2
  Image: AKSUbuntu-2404gen2containerd-202607.20.0
  Labels:
    environment: production
    workload: applications
  Max: 100
  Min: 2
  Mode: User
  Name: userpool
  State: Succeeded
  Taints: null
  Version: 1.35.6
Results of the positive placement test
  deployment "nodepool-test" successfully rolled out
Results of the negative taint test
   0/4 nodes are available: 2 node(s) didn't match Pod's node affinity/selector, 2 node(s) had untolerated taint(s). no new claims to deallocate, preemption: 0/4   nodes are available: 4 Preemption is not helpful for scheduling.
Upgrade channels and surge settings
  Surge settings updated to a max of 33% which is considered reasonable for a lab of this nature.
Any cost-driven differences between the lab and production design
  The lab design is more cost effective due to lower surge settings and pod scaling.
