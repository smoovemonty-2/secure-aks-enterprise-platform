Why separate system and user node pools?
  System pools runs the Kubernetes infrastructure while user node pools runs the business workloads. Imagine an application crashes and consumes all CPU resources. Without
  separate pools CoreDNS can become unresponsive, cluster add-ons may fail, monitoring agents can stop reporting, or the entire cluster becomes unstable. With separate pools,
  the Kubernetes control services remain isolated from application workloads, improving resilience and operational stability.
Why choose Azure CNI Overlay?
  The CNI Overlay conserves IP addresses, supports large clusters, integrates with Azure networking, works well with NSGs, Azure Firewall, and Private Link.
Why integrate AKS with Microsoft Entra ID?
  This provides centralized identity management, MFA, Conditional Access, auditing, lifecycle management, and least-privilege administration.
Why should monitoring be integrated from the beginning?
  Azure Monitor, Log Analytics, Defender for Cloud, and Sentinel provide continuous visibility, faster incident response, and support for compliance and forensic
  investigations which is useful to employ from the beginning as it can establish baselines and lessons to learn from.
What makes this architecture "enterprise-ready"?
  We have high availability through availability zones, separate node pools for more resilience and stability, centralized identity management, policy governance,
  supporting continuous monitoring, Defender integration, scalable networking, and future support for CI/CD pipelines and Infrastructure as Code (IaC).
