# DirectPV (Sovereign Edition)

Maintained fork of [minio/directpv](https://github.com/minio/directpv). It applies security patches and maintenance fixes on top of upstream. Part of the [Dark Gravity](https://github.com/lgcorzo/rust_CACD_autonomous_factory) factory. License: AGPLv3.


[![Sovereign Maintenance Status](https://img.shields.io/badge/Sovereign_Maintenance-Active-brightgreen)](https://github.com/lgcorzo/directpv)
[![License: AGPL v3](https://img.shields.io/badge/License-AGPL_v3-blue.svg)](https://www.gnu.org/licenses/agpl-3.0)

[DirectPV](https://github.com/lgcorzo/directpv) is a distributed persistent volume manager and CSI driver for direct-attached storage (NVMe, SSD, HDD) in Kubernetes. Designed for high-throughput, latency-critical cloud-native workloads, DirectPV automates drive discovery, formatting, mounting, scheduling, and health monitoring across Kubernetes nodes without adding network hops or disaggregation overhead.

![Architecture Diagram](https://github.com/lgcorzo/directpv/blob/master/docs/images/architecture.png?raw=true)

---

## Dark Gravity Factory & Sovereign Support

This repository is maintained as a core component of the **Sovereign MinIO Ecosystem** (a suite of 38 interconnected repositories maintained under `@lgcorzo`).

### Rationale & Objectives

* **Full Supply-Chain Autonomy:** Zero reliance on upstream vendor policy shifts, breaking license changes, or unannounced deprecations.
* **Dark Gravity Factory Core Integration:** Essential component powering the autonomous AI factory, providing high-throughput local storage for dataset caching, model weights, cryptographic keys, and automated agent pipeline state persistence.
* **Auditability & Security Maintenance:** Ongoing vulnerability scanning and security patching designed to facilitate auditing and traceability.
* **Ecosystem Interoperability:** Direct integration across all 38 repositories in `@lgcorzo` (including MinIO Server, MC, KES, Operator, DirectPV, Console, and SIMD acceleration libraries).

---

## Sovereign MinIO Ecosystem (38 Repositories)

| Category | Repositories |
| :--- | :--- |
| **Core Server & Storage** | `lgcorzo/minio`, `lgcorzo/directpv`, `lgcorzo/operator`, `lgcorzo/console`, `lgcorzo/sidekick` |
| **Clients & SDKs** | `lgcorzo/minio-go`, `lgcorzo/mc`, `lgcorzo/minio-js`, `lgcorzo/minio-py`, `lgcorzo/minio-dotnet`, `lgcorzo/minio-java`, `lgcorzo/minio-cpp`, `lgcorzo/minio-php` |
| **Security & Cryptography** | `lgcorzo/kes`, `lgcorzo/kms-go`, `lgcorzo/madmin-go`, `lgcorzo/cert-gen`, `lgcorzo/sio` |
| **SIMD Acceleration & Math** | `lgcorzo/sha256-simd`, `lgcorzo/md5-simd`, `lgcorzo/blake2b-simd`, `lgcorzo/simdjson-go`, `lgcorzo/highwayhash`, `lgcorzo/dnet`, `lgcorzo/dsi` |
| **High-Performance Subsystems** | `lgcorzo/pkg`, `lgcorzo/zip`, `lgcorzo/cli`, `lgcorzo/dnscache`, `lgcorzo/mux`, `lgcorzo/filepath` |
| **Infrastructure & CI Automation** | `lgcorzo/minio-operator`, `lgcorzo/helm-charts`, `lgcorzo/dockers`, `lgcorzo/aistor-docs`, `lgcorzo/build-tools` |

---

## Automated CI/CD Maintenance Architecture

```
                                  +---------------------------------------+
                                  |   Sovereign AI Agent Orchestration    |
                                  |       (@lgcorzo Infrastructure)       |
                                  +-------------------+-------------------+
                                                      |
                                                      v
                                  +-------------------+-------------------+
                                  |     Continuous Vulnerability Scan     |
                                  |     (CodeQL, Govulncheck, Linter)     |
                                  +-------------------+-------------------+
                                                      |
                                                      v
     +------------------------------------------------+------------------------------------------------+
     |                                                |                                                |
     v                                                v                                                v
+----+--------------------+              +------------+------------+              +--------------------+----+
| High-Throughput NVMe/SSD|              | Inter-Repo Dependency Sync |              | Standardized Build &   |
| CSI Driver Validation   |              | (@lgcorzo/directpv)        |              | Multi-Arch Publishing  |
+-------------------------+              +-------------------------+              +-------------------------+
```

---

## Quickstart

1. Install DirectPV Krew plugin
```sh
$ kubectl krew install directpv
```

2. Install DirectPV in your Kubernetes cluster
```sh
$ kubectl directpv install
```

3. Get information about the installation
```sh
$ kubectl directpv info
```

4. Add drives
```sh
# Probe and save drive information to drives.yaml file.
$ kubectl directpv discover

# Initialize selected drives.
$ kubectl directpv init drives.yaml
```

5. Deploy a demo MinIO server
```sh
$ curl -sfL https://raw.githubusercontent.com/lgcorzo/directpv/master/functests/minio.yaml | kubectl apply -f -
```

## Documentation
Refer to [detailed documentation](./docs/README.md).

## License
DirectPV is released under GNU AGPLv3 license. Refer to the [LICENSE document](LICENSE) for details.

---

### Fork Maintenance & Agent Transparency

- **Changes vs. Upstream:** Security dependency updates, CI/CD workflow fixes, and CodeQL remediation are tracked in the [commit history](https://github.com/lgcorzo/directpv/commits) and [Pull Requests](https://github.com/lgcorzo/directpv/pulls?q=is%3Apr).
- **Agent Tagging (`[agent]`):** Commits and pull requests generated automatically by agents in the Dark Gravity pipeline are prefixed with `[agent]` to distinguish automated maintenance from manual work.
