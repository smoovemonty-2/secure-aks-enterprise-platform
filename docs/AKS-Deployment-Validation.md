| Validation area      | Pass criteria                                  |
| -------------------- | ---------------------------------------------- |
| Provisioning         | `Succeeded`                                    |
| API access           | `kubectl cluster-info` succeeds                |
| Nodes                | All expected nodes are `Ready`                 |
| Node pools           | Correct mode, count, zones and autoscaling     |
| System pods          | No unexplained unhealthy pods                  |
| Entra authentication | User credentials work                          |
| Azure RBAC           | Effective access matches assigned role         |
| Local accounts       | `--admin` credentials are rejected             |
| Identity             | Managed identity is enabled                    |
| Network              | Expected plugin, mode, CIDRs and data plane    |
| DNS                  | Internal and external DNS tests succeed        |
| Monitoring           | `ama-logs` components healthy                  |
| Log Analytics        | AKS tables contain recent data                 |
| Azure Policy         | Add-on and Gatekeeper healthy                  |
| Defender             | Container plan and intended components enabled |
| Diagnostic settings  | Selected control-plane logs reach `law-prod`   |
| Workload scheduling  | Temporary deployment reaches ready state       |
