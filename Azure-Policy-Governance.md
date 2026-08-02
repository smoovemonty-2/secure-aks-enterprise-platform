What is Azure Policy?
  Azure Policy is an Azure governance service that evaluates resources against organizational rules and can audit, deny, modify, or automatically remediate deployments to
  enforce security and compliance standards.
What is the difference between Azure Policy and Azure RBAC?
  Azure Policy focuses on managing governance and configurations, whereas Azure Role-based Access Control (RBAC) focuses on managing identities and access. Think of Policy 
  as governing what can be deployed, resource compliance, blocking or modifying deploymens and think of RBAC as who can access which resources as well as evaluating user and service
  permissions, but not enforcing configurations.
When would you use Audit instead of Deny?
  You should use Audit when you do not want to disrupt current operations introducing new governance to an existing environment. You can still identify non-compliant resources
  or configurations without interrupting business operations. After reviewing the impact and remediated issues, you may then be ready to transition to utilizing Deny.
How does Azure Policy support NIST 800-53 and FedRAMP?
  Azure Policy helps organizations consistently enforce technical security controls, such as approved locations, encryption, logging, and tagging. By reducing configuration
  drift and providing compliance reporting, it supports continuous monitoring and the implementation of controls across frameworks like NIST SP 800-53 and FedRAMP.
Why should Azure Policy be configured before deploying AKS?
  This helps establish governance before workloads are deployed into production environments. This can help ensure all future resources are compliant with organizational
  standards the moment that are deployed, reducing configuration drift and minimizing security risks.
