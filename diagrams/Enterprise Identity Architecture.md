                    Microsoft Entra ID
                           │
                    MFA / Conditional Access
                           │
                           ▼
                Azure RBAC for Kubernetes
                           │
            ┌──────────────┼──────────────┐
            ▼              ▼              ▼
      AKS-Admins    AKS-Developers   AKS-Security
                           │
                           ▼
                  Kubernetes API Server
                           │
          ┌────────────────┼────────────────┐
          ▼                ▼                ▼
      ClusterRoles     Namespace Roles    Read-only Roles
