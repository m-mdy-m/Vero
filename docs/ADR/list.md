
# ADR list 

### پایه — Must 

1. `ADR-00_choose_language.md` — **Must** — چرا زبان(های) اصلی (Java/Kotlin, C, TS) انتخاب شدند.
2. `ADR-01_choose_database.md` — **Must** — انتخاب DB اصلی (Postgres / distributed DB / Redis) و دلیل.
3. `ADR-02_architecture_style.md` — **Must** — Monolith vs Microservices vs Modular Monolith vs Event-Driven.
4. `ADR-03_auth_design.md` — **Must** — AuthN/AuthZ approach (JWT vs OAuth2/OIDC vs SSO).
5. `ADR-04_choose_framework.md` — **Must** — web framework(s) (Spring / Ktor / Nest / Fastify) و دلیل.
6. `ADR-05_api_style.md` — **Must** — REST vs GraphQL vs gRPC; versioning policy.
7. `ADR-06_event_broker_choice.md` — **Must** — Kafka vs RabbitMQ vs NATS vs internal broker (برای event-driven).
8. `ADR-07_data_modeling_and_sharding.md` — **Must** — schema strategy, sharding/partitioning plan.
9. `ADR-08_secrets_management.md` — **Must** — Vault / KMS / env vars strategy.
10. `ADR-09_deployment_strategy.md` — **Must** — containers+k8s vs managed services, blue/green or canary.

### حیاتی — High (خیلی مهم)

11. `ADR-10_ci_cd_stack.md` — **High** — GitHub Actions vs GitLab CI vs other; pipeline policies.
12. `ADR-11_observability_stack.md` — **High** — logging/metrics/tracing choices (ELK/Prometheus+Grafana/Jaeger).
13. `ADR-12_monitoring_slo_sli.md` — **High** — SLO/SLI/SLA definitions and alerting thresholds.
14. `ADR-13_backup_and_recovery.md` — **High** — backup frequency, RTO/RPO targets.
15. `ADR-14_caching_strategy.md` — **High** — CDN + edge caching + redis caching patterns.
16. `ADR-15_rate_limiting_and_throttling.md` — **High** — global & per-user quotas and enforcement layer.
17. `ADR-16_messaging_and_retry_policy.md` — **High** — at-least-once vs at-most-once, DLQ handling.
18. `ADR-17_auth_identity_provider.md` — **High** — use internal identity vs external IdP (Auth0, Keycloak).

### معماری / توسعه — Medium

19. `ADR-18_schema_migration_strategy.md` — **Medium** — migrations tool (Flyway / Liquibase / custom) & versioning.
20. `ADR-19_api_contracts_and_contract_testing.md` — **Medium** — contract testing approach (Pact etc.).
21. `ADR-20_monorepo_vs_multirepo.md` — **Medium** — repo strategy برای backend/frontend/libs.
22. `ADR-21_dependency_management_and_security.md` — **Medium** — dependency policy, SBOM generation.
23. `ADR-22_code_style_and_review_policy.md` — **Medium** — linting, formatters, PR rules.
24. `ADR-23_feature_flag_strategy.md` — **Medium** — flags (LaunchDarkly/self-hosted) و lifecycle.
25. `ADR-24_task_queue_and_background_jobs.md` — **Medium** — worker model (Bull/RQ/Kafka consumers).

### امنیت و حریم خصوصی — Medium/High

26. `ADR-25_encryption_and_key_management.md` — **High** — keys lifecycle, KMS usage, rotation.
27. `ADR-26_data_retention_and_privacy.md` — **High** — retention periods, right-to-be-forgotten, DPIA.
28. `ADR-27_privacy_by_design.md` — **Medium** — default privacy settings, consent flows.
29. `ADR-28_incident_response_and_forensics.md` — **High** — IR playbook, logging retention for forensics.

### عملیات و infra — Medium

30. `ADR-29_infrastructure_as_code.md` — **Medium** — Terraform vs CloudFormation vs Pulumi.
31. `ADR-30_cloud_provider_choice.md` — **Medium** — AWS/GCP/Azure or multi-cloud vs on-prem.
32. `ADR-31_container_runtime.md` — **Medium** — containerd vs docker, runtime constraints.
33. `ADR-32_network_topology_and_vpc.md` — **High** — network segmentation, peering, ingress/egress controls.
34. `ADR-33_cicd_artifacts_storage.md` — **Medium** — artifact registry (Docker registry, Maven/NPM).
35. `ADR-34_cost_management.md` — **Medium** — cost monitoring & optimization policy.

### تعامل با سخت‌افزار / Offline-first / mobile — Medium/Low

36. `ADR-35_offline_sync_and_conflict_resolution.md` — **High** (برای TALKEN) — sync model, CRDT vs OT vs last-write.
37. `ADR-36_embedded_node_integration.md` — **Medium** — protocol for node ↔ cloud, firmware update model.
38. `ADR-37_ota_and_firmware_update_strategy.md` — **Medium** — secure updates, rollback.
39. `ADR-38_wireless_protocol_choice.md` — **Medium** — BLE / Wi-Fi-direct / LoRa for TALKEN nodes.

### تست / کیفیت — Medium

40. `ADR-39_testing_strategy.md` — **Medium** — unit/integration/e2e/property-based testing.
41. `ADR-40_performance_testing_and_benchmarking.md` — **Medium** — load test tooling & acceptance thresholds.
42. `ADR-41_security_testing_and_pentest.md` — **High** — pentest cadence, bug-bounty policy (if any).

### قراردادها و حقوقی — Medium

43. `ADR-42_open_source_and_license_policy.md` — **Medium** — license for repos (MIT/Apache/Proprietary).
44. `ADR-43_third_party_services_and_vendor_lockin.md` — **Medium** — criteria for 3rd-party usage.
45. `ADR-44_compliance_and_regulatory.md` — **High** — GDPR, export control, radio certifications (if HW).

### توسعه تیمی و فرآیند — Low/Medium

46. `ADR-45_oncall_and_rota_policy.md` — **Medium** — on-call expectations, pager policy.
47. `ADR-46_release_and_versioning_policy.md` — **Medium** — semver, release branches, changelog.
48. `ADR-47_documentation_and_docs_ci.md` — **Low** — docs toolchain and CI for docs.
49. `ADR-48_contributor_guidelines.md` — **Low** — CONDUCT, CONTRIBUTING.md rules.

### Edge / future / research — Low

50. `ADR-49_experimental_tech_stack.md` — **Low** — trialing Rust/Wasmtime/edge compute choices.
51. `ADR-50_long_term_data_archive_and_analytics.md` — **Low** — DW/OLAP choice for analytics (Redshift/BigQuery).

