Cluster Overview
  Cluster name: aks-prod-eastus2, Region: East US 2, Kubernetes version: 1.35.6, node configuration: 2 node pools (system and user) 2 nodes each with a size of
  Standard_D2ds_v7.
Identity Decisions:
  Microsoft Entra integration, 
  Azure RBAC as Kuberenetes RBAC controls permissions inside the cluster while Azure RBAC integrates those permissions with Entra ID, benefits include MFA, Auditing,
  consistent governance across resources and Kuberenetes, etc.
  Disabled local accounts as they can bypass centralized identity management.
  Managed identity as it eliminates the need to store credentials in code or configuration. Azure automatically manages issuing and rotating credentials which helps
  reduce the risk of exposure and simplifies application authentication to Azure services.
Networking Decisions
  Azure CNI Overlay provides better integration with Azure networking, makes it easier to apply Network Security Groups (NSGs), has support for Azure Firewall, and
  better scalability.
  The subnet layout helps segment current and future resources for simpler management and better security as resources are properly separated based on function 
  and purpose.
  We mad the cluster public initially to simplify our learning on this project, in a true production environment it is advisable to make it private.
Monitoring Decisions
  We enabled Azure Monitor, Log Analytics Workspace, and Azure Policy add-on so we can monitor our cluster, logs can flow into the Log Analytics Workspace which allows
  for centralized logging and collection of essential information such as cluster health, incidents to investigate, integrate with Sentinel for threat detection and
  hunting, etc.
Security Tradeoffs
  One major tradeoff was making the API server public for simplified learning. We would want to ensure our cluster is not reachable publicly as this creates a greater
  attack surface for malicious actors.
