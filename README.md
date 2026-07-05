## Hi, I'm Anurag 👋

I'm a software engineer who likes building infrastructure that's **fast, cheap to run, and honest about its trade-offs** — mostly **Rust**, distributed systems, and observability done right: storage you own, costs you can see, no vendor lock-in.

You'll usually find me somewhere inside a query engine or a storage tier. My main account is **[@anurag-bhatt1](https://github.com/anurag-bhatt1)**.

### 🌿 Currently building — Verdigris

> *The layer your infrastructure leaves behind.*

[![Docs](https://img.shields.io/badge/docs-verdigris-2E8E7F?style=flat-square)](https://explise.github.io/verdigris-docs/) &nbsp;![Rust](https://img.shields.io/badge/built%20with-Rust-B06A3B?style=flat-square) &nbsp;![Engine](https://img.shields.io/badge/query-Apache%20DataFusion-184F47?style=flat-square) &nbsp;![License](https://img.shields.io/badge/license-Apache--2.0-5C9A7A?style=flat-square)

A plug-and-play, **S3-native log storage & query engine** in Rust — a self-hostable log platform that keeps your log data in **your own cloud account**. Deploy it on EKS, point your existing **Vector / Fluent Bit / OpenTelemetry** pipeline at it, and query logs **in place** as Parquet in your own S3 bucket. No vendor cloud in the path, no rehydration toll, no proprietary query language.

**What makes it different**

- **Data sovereignty** — logs never leave your AWS account; no per-GB ingestion margin.
- **No rehydration tax** — queries read Parquet straight from S3; cold logs stay live, you pay compute only when you query.
- **Storage cheap, compute provisioned** — priced by bytes in S3; query speed is a dial. Severity sets *placement*, never *price*.
- **Cost made legible** — a pre-query estimate before any Glacier scan, so no surprise bills.
- **One `helm install`, done** — a single binary + Helm chart on EKS + S3, via IRSA (no static keys).

Native OTLP + Vector/Fluent Bit ingest · SQL + a search DSL over Apache DataFusion · severity tiering with S3 lifecycle · small-file compaction · a cost estimator · continuous alerting · an Arrow-native web UI.

**[📖 Read the docs →](https://explise.github.io/verdigris-docs/)**
