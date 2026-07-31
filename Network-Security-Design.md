Why did you choose a /16 VNet with /24 subnets?
  A /16 Vnet allows for 65,536 IP addresses which gives the environment room to grow over time. In enterprise environments new services or assets are added often,
  perhaps new AKS clusters, firewalls, databases, private endpoints, etc. A /24 subnet is usually enough to support most workloads while keeping network segmentation
  straightforward. For security purposes, eparate subnets allow different Network Security Groups (NSGs), route tables, and policies to be applied based on the 
  purpose of each workload, supporting the principle of least privilege and limiting lateral movement.

Why is the ingress subnet separated from the AKS node subnet?
  This is to isolate externally facing components from the Kubernetes worker nodes. Ingress subnets hosts resources such as an Application Gateway or NGINX controller, 
  these are naturally exposed to more risk than internal workloads. The AKS node subnet Kubernetes worker nodes that run the application containers. Keeping these nodes in a 
  separate subnet reduces the attack surface and helps prevent an attacker who compromises an ingress component from easily reaching the worker nodes. 
  This separation also allows:
    Different NSG rules for public-facing and internal resources.
    Independent routing and firewall policies.
    Easier monitoring and troubleshooting.
    Compliance with network segmentation requirements commonly found in NIST 800-53 and FedRAMP environments.

Why are Private Endpoints placed in their own subnet?
  Placing Private Endpoints in a dedicated subnet provides several advantages:
    Centralized management of all private connectivity.
    Easier application of NSGs and route tables.
    Simplified monitoring and troubleshooting.
    Better scalability as additional private endpoints are added.
    Clear separation between application traffic and infrastructure services.

  For regulated environments like DoD or FedRAMP, using Private Endpoints reduces exposure by eliminating the need for public service endpoints whenever possible.
  For example, instead of an AKS cluster pulling images from a publicly accessible Container Registry, it can communicate with the registry entirely over 
  Microsoft's private backbone.

Why should Kubernetes worker nodes avoid public IP addresses?
  Kubernetes worker nodes should not have public IP addresses because they do not need to be directly accessible from the internet. 
  Exposing worker nodes publicly increases the attack surface by allowing attackers to attempt malicious activity such as SSH brute force attacks, OS exploitation, 
  Kubernetes service discovery, malware deployment, etc.
  Instead, users should access applications through a controlled ingress point, such as an Application Gateway or Ingress Controller, while administrators manage the cluster through secure methods like:
    Azure Bastion.
    VPN connections.
    Private API Server.
    Azure RBAC and Microsoft Entra ID authentication.
  This design follows the principle of least exposure, ensuring that only resources intended to receive external traffic are internet-facing.

How does this design support a FedRAMP or DoD cloud environment?
  This architecture aligns with many security principles found in FedRAMP Moderate and DoD cloud environments by emphasizing network segmentation,
  centralized monitoring, identity-based access control, and defense in depth.
  Key aspects include:
    Network segmentation: Separate subnets isolate workloads and reduce the risk of lateral movement.
    Least privilege: Azure RBAC and Kubernetes RBAC ensure users and services receive only the permissions they require.
    Private connectivity: Private Endpoints keep sensitive communications on Microsoft's private network rather than the public internet.
    Centralized logging and monitoring: Azure Monitor, Log Analytics, Microsoft Defender for Cloud, and Microsoft Sentinel provide continuous monitoring and support incident response.
    Security policies: Azure Policy can enforce encryption, approved VM sizes, mandatory tags, and other organizational standards.
    Threat detection: Microsoft Defender for Containers and Microsoft Defender for Cloud provide vulnerability assessments and runtime threat detection.
    Governance: Resource groups, tagging, and naming conventions improve accountability, auditing, and operational consistency.
  While this lab does not achieve FedRAMP authorization on its own, it incorporates architectural practices that support compliance efforts and map well to controls 
  found in frameworks such as NIST SP 800-53, including access control (AC), audit and accountability (AU), configuration management (CM), system and 
  communications protection (SC), and system and information integrity (SI).
