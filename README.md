# Advait Sane

I build backend and distributed systems, mostly in Java and Spring. I care most about how a system
behaves when things go wrong. I'd rather measure a resilience claim with a load test or a fault
injection than assume it, and I write down the decisions and tradeoffs along the way.

## Featured project

**[movie-recommendation-system](https://github.com/advaitsane/movie-recommendation-system)** rebuilds
MongoDB's `mflix` sample monolith as five Spring Boot domain services behind an API gateway:
- **Architecture:** a CQRS search read model fed by Kafka, an outbox for review events, and a
  recommendation service that blends content and collaborative signals and falls back when either
  is down.
- **Infrastructure:** api-gateway with JWT enforcement, rate limiting and circuit breakers, plus
  OpenTelemetry tracing and Prometheus/Grafana metrics.
- **Verified under failure:** k6 load tests and chaos experiments (killed dependencies, injected
  latency, OOM kills) found real gaps: a health check that missed a database outage, circuit
  breakers that could never open, and timeout budgets that didn't line up. Each gap is fixed and
  recorded in an [ADR](https://github.com/advaitsane/movie-recommendation-system/tree/main/docs/adr).
- **Built in public:** the repo went up one
  [pull request per build step](https://github.com/advaitsane/movie-recommendation-system/pulls?q=is%3Apr+is%3Amerged),
  so the history shows how it was built and why.

Stack: Java 25 · Spring Boot 4 · Spring Cloud Gateway · Resilience4j · Kafka · MongoDB (Atlas
Search, vector search) · PostgreSQL · Redis · Docker · k6 · GitHub Actions

## Currently

Moving movie-recommendation-system onto Kubernetes, replacing config-server and configured URLs
with ConfigMaps and Service DNS, and recording each step in an ADR.

## Contact

[LinkedIn](https://www.linkedin.com/in/advait-sane/)
