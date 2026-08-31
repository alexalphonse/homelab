# Kubernetes Homelab — GitOps Infrastructure Platform

A self-hosted Kubernetes platform managed using GitOps principles, with
declarative configuration for cluster infrastructure, platform services,
and application workloads.

The goal of this project is to build and operate a production-style
infrastructure environment while learning and applying Kubernetes,
Linux, GitOps, networking, storage, observability, and infrastructure
automation.

---

## Architecture

```text
                         ┌─────────────────────┐
                         │       GitHub        │
                         │   Source of Truth   │
                         └──────────┬──────────┘
                                    │
                                    │ Git
                                    ▼
                         ┌─────────────────────┐
                         │       FluxCD        │
                         │ GitOps Reconciliation│
                         └──────────┬──────────┘
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │     Kubernetes      │
                         │     Talos Linux     │
                         └──────────┬──────────┘
                                    │
              ┌─────────────────────┼─────────────────────┐
              │                     │                     │
              ▼                     ▼                     ▼
       ┌─────────────┐       ┌─────────────┐       ┌─────────────┐
       │ Networking  │       │   Storage   │       │ Monitoring  │
       ├─────────────┤       ├─────────────┤       ├─────────────┤
       │  Traefik    │       │  Longhorn   │       │ Prometheus  │
       │  MetalLB    │       │             │       │  Grafana    │
       │ cert-manager│       │             │       │             │
       └─────────────┘       └─────────────┘       └─────────────┘
                                   
                         ┌─────────────────────┐
                         │     Applications    │
                         ├─────────────────────┤
                         │ Forgejo             │
                         │ n8n                 │
                         │ Homepage            │
                         │ Affine              │
                         │ KubeVirt VMs        │
                         └─────────────────────┘
