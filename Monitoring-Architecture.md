Why should monitoring be deployed before workloads?
  One majore mistake that is common when deploying infrastructure is enabling monitoring or logging after workloads have already been deployed. This can create
  gaps where security events get missed, audit logs are not retained, there is no performance basleine to reference, and making incident response more difficult.
What is the difference between Azure Monitor and Log Analytics?
  Azure monitor stores and manages telemetry while Log Analytics is a central data repository for storing logs that can be queried and analyzed using Kusto Query Langugage
  (KQL).
Why centralize logs?
  Centralizing logs can enable faster incident response, make it easier to hunt threats, simplify compliance reporting, integration with Microsoft Sentinel and Defender,
  and consistent operational visibility.
Why separate monitoring resources into rg-monitoring?
  Easier Role-based Access Control (RBAC) management, separation of duties, independent lifecycle management, helps simplify cost tracking, and reduces the risk of 
  accidental deletions.
