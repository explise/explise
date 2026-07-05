<h1 align="center">Verdigris</h1>
<p align="center"><em>The layer your infrastructure leaves behind.</em></p>

<p align="center">
  <a href="https://explise.github.io/verdigris-docs/"><img alt="Docs" src="https://img.shields.io/badge/docs-verdigris-2E8E7F?style=flat-square"></a>
  <img alt="Built with Rust" src="https://img.shields.io/badge/built%20with-Rust-B06A3B?style=flat-square">
  <img alt="Engine" src="https://img.shields.io/badge/query-Apache%20DataFusion-184F47?style=flat-square">
  <img alt="License" src="https://img.shields.io/badge/license-Apache--2.0-5C9A7A?style=flat-square">
</p>

**Verdigris** is a plug-and-play, **S3-native log storage & query engine** written in Rust — a self-hostable log platform that keeps your log data in **your own cloud account**. Deploy it into your EKS cluster, point your existing **Vector / Fluent Bit / OpenTelemetry** pipeline at it, and query logs **in place** as Parquet in your own S3 bucket. No vendor cloud in the path, no rehydration toll, no proprietary query language.

### Why it's different

- 🟩 **Data sovereignty** — logs never leave your AWS account; no per-GB ingestion margin on every byte.
- 🟩 **No rehydration tax** — queries read Parquet straight out of S3, in place. Cold logs are always live — you pay compute only when you actually query.
- 🟩 **Storage cheap, compute provisioned** — priced by bytes in S3; query speed is a dial you turn. Severity decides *placement*, never *price*.
- 🟩 **Cost made legible** — a pre-query estimator tells you *"this scans ~X GB from Glacier, ~$Y — continue?"* before you run it.
- 🟩 **One `helm install`, done** — a single binary + Helm chart brings it up on EKS + S3, writing to your bucket via IRSA (no static keys).

### How it works

```
   pods on EKS
       │  (stdout/stderr · OTLP)
       ▼
   Vector / Fluent Bit / OTel Collector      ← ingest what your apps already emit
       │
       ▼
   Verdigris ingest ──►  Parquet + catalog in YOUR S3 bucket
       │                      hot → warm → cold, aged by S3 lifecycle
       ▼
   Verdigris query engine (Apache DataFusion)  ← query in place, no rehydration
       │
       ▼
   SQL + search DSL  ·  Web UI  ·  Grafana  ·  continuous alerting
```

### What's inside

Native **OTLP** + Vector/Fluent Bit ingest · **SQL** and a concise search DSL over Apache DataFusion · severity-based **tiering** with S3 lifecycle · small-file **compaction** · a pre-query **cost estimator** · continuous **alerting** · an Arrow-native web UI · one-command **Helm** deploy.

<p align="center">
  <b><a href="https://explise.github.io/verdigris-docs/">📖 Read the docs →</a></b>
</p>
