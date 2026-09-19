<!-- SPDX-License-Identifier: Apache-2.0 AND CC-BY-4.0 -->
<!-- Copyright (c) 2026 NVIDIA Corporation. All rights reserved. -->

# NVIDIA Agent Skills

**Official, NVIDIA-verified skills for AI agents.**

[![NVIDIA](https://img.shields.io/badge/NVIDIA-Verified-76B900?style=flat&logo=nvidia&logoColor=white)](https://nvidia.com)
[![Agent Skills Spec](https://img.shields.io/badge/Agent%20Skills-Specification-blue)](https://agentskills.io)
[![License](https://img.shields.io/badge/License-Apache%202.0%20%2B%20CC--BY--4.0-green.svg)](LICENSE)

> 📖 **Docs:** [docs.nvidia.com/skills](https://docs.nvidia.com/skills) &nbsp;·&nbsp;
> 📺 **Livestream:** [From Vulnerable to Verified](https://www.youtube.com/watch?v=sVpKonYJ4D4&list=PL5B692fm6--vEL0FwctKghCpyEnBGAQJA&index=1) &nbsp;·&nbsp;
> 📝 **Blog:** [NVIDIA Verified Agent Skills: Capability Governance for AI Agents](https://developer.nvidia.com/blog/nvidia-verified-agent-skills-provide-capability-governance-for-ai-agents/)

---

Skills are portable instruction sets that teach AI agents how to use NVIDIA CUDA-X libraries, AI Blueprints, and platform tools correctly. This repository is a catalog: skills are maintained in their respective product repos and mirrored here daily via an automated sync pipeline. We are making NVIDIA skills available publicly and building this catalog in the open; see the [Roadmap](#roadmap) for what is planned next.

---

## Quickstart

Install NVIDIA skills with the default [`skills` CLI](https://github.com/vercel-labs/skills) flow:

```bash
npx skills add nvidia/skills
```

The CLI runs through `npx` and prompts you to choose a skill and install destination. You do not need to clone this repo or copy skill folders by hand.

The skill is available the next time your agent loads skills and encounters a relevant task. For example, ask your agent to "solve a linear programming problem with cuOpt" and the skill guides it through the cuOpt Python API.

### Install One Skill Without Prompts

Use this when you already know the skill name and want to skip prompts.

```bash
npx skills add nvidia/skills --skill cuopt-numerical-optimization-api-python --yes
```

Replace `cuopt-numerical-optimization-api-python` with any skill name from the [Skill Catalog](#skill-catalog).

### Install for a Specific Agent

Use `--agent` to target a specific AI coding agent. These are common client targets; for the full list of supported clients, see the [`skills` CLI Supported Agents table](https://github.com/vercel-labs/skills#supported-agents).

**Claude Code**

```bash
npx skills add nvidia/skills --skill cuopt-numerical-optimization-api-python --agent claude-code
```

**Codex**

```bash
npx skills add nvidia/skills --skill cuopt-numerical-optimization-api-python --agent codex
```

**Cursor**

```bash
npx skills add nvidia/skills --skill cuopt-numerical-optimization-api-python --agent cursor
```

**Kiro**

```bash
npx skills add nvidia/skills --skill cuopt-numerical-optimization-api-python --agent kiro-cli
```

Use `--agent` more than once to install the same skill into multiple agents.

```bash
npx skills add nvidia/skills \
  --skill cuopt-numerical-optimization-api-python \
  --agent claude-code \
  --agent codex \
  --agent cursor \
  --agent kiro-cli
```

### Browse the Catalog

Use this when you want to see available NVIDIA skills before installing anything.

```bash
npx skills add nvidia/skills --list
```

For non-interactive installs, global installs, agent-specific installs, updates, removals, and fallback manual copying, see [Advanced installation](docs/advanced-install.mdx).

---

## Skill Catalog

<!-- skills-table-start -->
| Product | Description | Skills | Catalog | Source | Version |
|---------|-------------|:------:|---------|--------|---------|
| **AIQ** | NVIDIA AI-Q Blueprint - deploy local AI-Q services and run shallow or deep research workflows as agent skills. | 2 | [`skills/aiq-research/`](skills/aiq-research) | [Source](https://github.com/NVIDIA-AI-Blueprints/aiq/tree/develop/skills/aiq-research) | [`bf4e67d`](https://github.com/NVIDIA-AI-Blueprints/aiq/commit/bf4e67d1564ef8d2ec8f65b5f9001e512befc095) · 2026-08-28 |
| **CUDA-Q** | CUDA Quantum — onboarding guide for installation, test programs, GPU simulation, QPU hardware, and quantum applications. | 1 | [`skills/cudaq-guide/`](skills/cudaq-guide) | [Source](https://github.com/NVIDIA/cuda-quantum/tree/main/skills/cudaq-guide) | [`03bd606`](https://github.com/NVIDIA/cuda-quantum/commit/03bd6067e270e309ec09cc34b8411df015ff02d5) · 2026-09-18 |
| **cuDF** | Official NVIDIA-authored guidance for NVIDIA cuDF GPU DataFrames, pandas acceleration, dask-cuDF, ETL, joins, groupby, CSV/Parquet I/O, nullable semantics, and multi-GPU DataFrame workloads. | 1 | [`skills/accelerated-computing-cudf/`](skills/accelerated-computing-cudf) | [Source](https://github.com/rapidsai/cudf/tree/main/skills/accelerated-computing-cudf) | [`cba0893`](https://github.com/rapidsai/cudf/commit/cba08937526d54de1b15ded7b0b2769ee3d43759) · 2026-09-19 |
| **cuOpt** | GPU-accelerated optimization — vehicle routing, linear programming, quadratic programming, installation, server deployment, and developer tools. | 12 | [`skills/cuopt-developer/`](skills/cuopt-developer) | [Source](https://github.com/NVIDIA/cuopt/tree/main/skills/cuopt-developer) | [`d5de274`](https://github.com/NVIDIA/cuopt/commit/d5de274d4f9def7223ceff1af9f19e32ab9b9748) · 2026-09-19 |
| **cuPyNumeric** | NumPy and SciPy on multi-node multi-GPU systems — skills to help with installing cuPyNumeric, migrating existing NumPy code, and doing parallel I/O | 4 | [`skills/cupynumeric-hdf5/`](skills/cupynumeric-hdf5) | [Source](https://github.com/nv-legate/cupynumeric/tree/main/skills/cupynumeric-hdf5) | [`4381d52`](https://github.com/nv-legate/cupynumeric/commit/4381d523f68f3790f26df05d5b5c9769aa61237a) · 2026-09-04 |
| **DALI** | GPU-accelerated data loading and processing with NVIDIA DALI. | 1 | [`skills/dali-dynamic-mode/`](skills/dali-dynamic-mode) | [Source](https://github.com/NVIDIA/DALI/tree/main/skills/dali-dynamic-mode) | [`f362c31`](https://github.com/NVIDIA/DALI/commit/f362c31e1fec7c7f125122cca866c4b0d9a46105) · 2026-09-18 |
| **DeepStream** | Agentic skills for guided DeepStream development. | 2 | [`skills/deepstream-dev/`](skills/deepstream-dev) | [Source](https://github.com/NVIDIA-AI-IOT/DeepStream_Coding_Agent/tree/main/skills/deepstream-dev) | [`3daf16a`](https://github.com/NVIDIA-AI-IOT/DeepStream_Coding_Agent/commit/3daf16ae5168dd685608bb929fb4f5513f308045) · 2026-05-28 |
| **Dynamo** | NVIDIA Dynamo deployment bring-up on Kubernetes — pick and deploy recipes, start router modes, validate disagg NIXL/UCX/NCCL interconnect, and triage day-2 failures. | 4 | [`skills/dynamo-interconnect-check/`](skills/dynamo-interconnect-check) | [Source](https://github.com/ai-dynamo/dynamo/tree/main/skills/dynamo-interconnect-check) | [`5593e88`](https://github.com/ai-dynamo/dynamo/commit/5593e8857c508bebce7259e107a85c57cd142fd8) · 2026-09-19 |
| **Earth2Studio** | Open-source deep-learning framework for exploring, building and deploying AI weather/climate workflows. | 4 | [`skills/earth2studio-data-fetch/`](skills/earth2studio-data-fetch) | [Source](https://github.com/NVIDIA/earth2studio/tree/main/skills/earth2studio-data-fetch) | [`f0da758`](https://github.com/NVIDIA/earth2studio/commit/f0da75829b623c3c2280a3a8394c2359d5fb9beb) · 2026-09-15 |
| **Megatron-Core** | Large-scale distributed training — model parallelism, pipeline parallelism, and mixed precision. | 5 | [`skills/mcore-create-issue/`](skills/mcore-create-issue) | [Source](https://github.com/NVIDIA/Megatron-LM/tree/main/skills/mcore-create-issue) | [`2085eac`](https://github.com/NVIDIA/Megatron-LM/commit/2085eac401ea5b56bfa9a9ff5e9463dd5e39da8e) · 2026-09-19 |
| **NeMo AutoModel** | NeMo AutoModel - PyTorch-native distributed training for LLMs/VLMs with Hugging Face support, recipes, launchers, and validation workflows. | 4 | [`skills/nemo-automodel-distributed-training/`](skills/nemo-automodel-distributed-training) | [Source](https://github.com/NVIDIA-NeMo/Automodel/tree/main/skills/nemo-automodel-distributed-training) | [`e2c47c5`](https://github.com/NVIDIA-NeMo/Automodel/commit/e2c47c5bcb3e6e0224adace569a1ded7872c002f) · 2026-09-18 |
| **NeMo MBridge** | NeMo MBridge - PyTorch-native bridge between Hugging Face and Megatron-Core for checkpoint conversion, training recipes, and NVIDIA GPU performance workflows. | 20 | [`skills/nemo-mbridge-mlm-bridge-training/`](skills/nemo-mbridge-mlm-bridge-training) | [Source](https://github.com/NVIDIA-NeMo/Megatron-Bridge/tree/main/skills/nemo-mbridge-mlm-bridge-training) | [`18ecd5f`](https://github.com/NVIDIA-NeMo/Megatron-Bridge/commit/18ecd5f47fc5e06e3dfec1f6792160861af0a616) · 2026-09-18 |
| **NeMo Platform** | NeMo Platform brings NVIDIA NeMo libraries together under one CLI, Python SDK, and web UI | 2 | [`skills/nemo-evaluator-plugin/`](skills/nemo-evaluator-plugin) | [Source](https://github.com/NVIDIA-NeMo/nemo-platform/tree/main/skills/nemo-evaluator-plugin) | [`8ee4ab1`](https://github.com/NVIDIA-NeMo/nemo-platform/commit/8ee4ab1af6d17e2587322e84f7360528f97d038b) · 2026-09-19 |
| **NeMo Retriever** | NeMo Retriever - deploy NeMo Retriever Library locally, extract information from corpus of data, and answer questions against the corpus. | 1 | [`skills/nemo-retriever/`](skills/nemo-retriever) | [Source](https://github.com/NVIDIA/NeMo-Retriever/tree/main/skills/nemo-retriever) | [`064d394`](https://github.com/NVIDIA/NeMo-Retriever/commit/064d39490ce0e4b4eb3574bda65fbc55ed3bea93) · 2026-09-18 |
| **NeMo-RL** | RLHF training on Ray — GRPO, DPO, and SFT for LLMs and VLMs with FSDP2 and Megatron-Core. | 5 | [`skills/NeMo-RL/`](skills/NeMo-RL) | [Source](https://github.com/NVIDIA-NeMo/RL/tree/main/skills) | [`b7a4d95`](https://github.com/NVIDIA-NeMo/RL/commit/b7a4d95d9099bae2b7f3713cc402aed3f21aef8d) · 2026-09-18 |
| **NemoClaw** | Secure agent sandboxing — run OpenClaw inside NVIDIA OpenShell with managed inference, policy management, remote deployment, sandbox monitoring. | 10 | [`skills/nemoclaw-user-agent-skills/`](skills/nemoclaw-user-agent-skills) | [Source](https://github.com/NVIDIA/NemoClaw/tree/main/skills/nemoclaw-user-agent-skills) | [`e38726c`](https://github.com/NVIDIA/NemoClaw/commit/e38726c8d792dc99c03ce3a29619ed21f7d32d34) · 2026-09-18 |
| **Nemotron** | Author end-to-end model development, customization, evaluation, and deployment pipelines using the NVIDIA AI stack. | 2 | [`skills/nemotron-customize/`](skills/nemotron-customize) | [Source](https://github.com/NVIDIA-NeMo/Nemotron/tree/main/skills/nemotron-customize) | [`8749344`](https://github.com/NVIDIA-NeMo/Nemotron/commit/8749344f8ccefd50181c56b013ddc5c8a6154a8c) · 2026-09-11 |
| **NVIDIA Digital Health Examples** | Agent skills for the clinical ASR evaluation flywheel — term curation, synthetic clinical-speech benchmark generation, KER (Keyword Error Rate) scoring, and fine-tune guidance. | 4 | [`skills/digital-health-clinical-asr-setup/`](skills/digital-health-clinical-asr-setup) | [Source](https://github.com/NVIDIA/digital-health-examples/tree/main/skills/digital-health-clinical-asr-setup) | [`b0ef844`](https://github.com/NVIDIA/digital-health-examples/commit/b0ef8449ff32c4d85f954e7f2a4478ff80056fb7) · 2026-06-26 |
| **Physical AI** | Physical AI development — Omniverse USD/Kit workflows (CAD-to-SimReady conversion, realtime viewer orchestration, USD performance tuning), infrastructure setup for synthetic data generation and resilient scaling, and neural reconstruction (NuRec/NRE). | 5 | [`omniverse-cad-to-simready/`](skills/omniverse-cad-to-simready) · [`omniverse-realtime-viewer/`](skills/omniverse-realtime-viewer) · [`omniverse-usd-performance-tuning/`](skills/omniverse-usd-performance-tuning) · [`physical-ai-infrastructure-setup-and-resilient-scaling/`](skills/physical-ai-infrastructure-setup-and-resilient-scaling) · [`physical-ai-neural-reconstruction/`](skills/physical-ai-neural-reconstruction) | — | — |
| **PhysicsNeMo** | NVIDIA PhysicsNeMo - Open-source deep-learning framework for building, training, and fine-tuning deep learning models using state-of-the-art Physics-ML methods. | 1 | [`skills/physicsnemo-discover/`](skills/physicsnemo-discover) | [Source](https://github.com/NVIDIA/physicsnemo/tree/main/skills/physicsnemo-discover) | [`94dbdf8`](https://github.com/NVIDIA/physicsnemo/commit/94dbdf829d1a4e93e3f31ecb77713392c471388e) · 2026-09-18 |
| **RAG Blueprint** | RAG pipeline — deploy, configure, troubleshoot, and manage retrieval augmented generation with Docker Compose or Helm. | 3 | [`skills/rag-blueprint/`](skills/rag-blueprint) | [Source](https://github.com/NVIDIA-AI-Blueprints/rag/tree/develop/skills/rag-blueprint) | [`cc84e6a`](https://github.com/NVIDIA-AI-Blueprints/rag/commit/cc84e6ac93801acb758570e3415ce355b550cf36) · 2026-08-20 |
| **Skill Card Generator** | Reads an agent skill's source files and produces a skill card plus a review table. Use when a skill directory exists and a governance card needs to be generated or updated. | 1 | [`skills/skill-card-generator/`](skills/skill-card-generator) | [Source](https://github.com/NVIDIA/Trustworthy-AI/tree/main/skills/skill-card-generator) | [`07d2ae7`](https://github.com/NVIDIA/Trustworthy-AI/commit/07d2ae7d3d080a20cebb56661162eea5c46a8639) · 2026-09-09 |
| **TileGym** | Tile-based GPU programming — adding new kernels, cross-framework conversion, and performance optimization. | 7 | [`skills/tilegym-adding-cutile-kernel/`](skills/tilegym-adding-cutile-kernel) | [Source](https://github.com/NVIDIA/TileGym/tree/main/skills/tilegym-adding-cutile-kernel) | [`ec339c0`](https://github.com/NVIDIA/TileGym/commit/ec339c0dbac3efe61e73ac2b782f818d253eaff2) · 2026-09-17 |
<!-- skills-table-end -->

---

## Getting Help & Contributing

For skill-related issues, feature requests, new skill ideas, discussions, and contributions — use the source repo for the relevant product:

<!-- help-table-start -->
| Product | Issues | Discussions | Contributing | Security |
|---------|--------|-------------|--------------|----------|
| **AIQ** | [Issues](https://github.com/NVIDIA-AI-Blueprints/aiq/issues) | [Discussions](https://github.com/NVIDIA-AI-Blueprints/aiq/discussions) | [Contributing](https://github.com/NVIDIA-AI-Blueprints/aiq/blob/develop/CONTRIBUTING.md) | [Security](https://github.com/NVIDIA-AI-Blueprints/aiq/blob/develop/SECURITY.md) |
| **CUDA-Q** | [Issues](https://github.com/NVIDIA/cuda-quantum/issues) | [Discussions](https://github.com/NVIDIA/cuda-quantum/discussions) | [Contributing](https://github.com/NVIDIA/cuda-quantum/blob/main/Contributing.md) | [Security](https://github.com/NVIDIA/cuda-quantum/blob/main/SECURITY.md) |
| **cuDF** | [Issues](https://github.com/rapidsai/cudf/issues) | [Discussions](https://github.com/rapidsai/cudf/discussions) | [Contributing](https://github.com/rapidsai/cudf/blob/main/CONTRIBUTING.md) | [Security](https://github.com/rapidsai/cudf/blob/main/SECURITY.md) |
| **cuOpt** | [Issues](https://github.com/NVIDIA/cuopt/issues) | [Discussions](https://github.com/NVIDIA/cuopt/discussions) | [Contributing](https://github.com/NVIDIA/cuopt/blob/main/CONTRIBUTING.md) | [Security](https://github.com/NVIDIA/cuopt/blob/main/SECURITY.md) |
| **cuPyNumeric** | [Issues](https://github.com/nv-legate/cupynumeric/issues) | [Discussions](https://github.com/nv-legate/cupynumeric/discussions) | [Contributing](https://github.com/nv-legate/cupynumeric/blob/main/CONTRIBUTING.md) | [Security](https://github.com/nv-legate/cupynumeric/blob/main/SECURITY.md) |
| **DALI** | [Issues](https://github.com/NVIDIA/DALI/issues) | [Discussions](https://github.com/NVIDIA/DALI/discussions) | [Contributing](https://github.com/NVIDIA/DALI/blob/main/CONTRIBUTING.md) | [Security](https://github.com/NVIDIA/DALI/blob/main/SECURITY.md) |
| **DeepStream** | [Issues](https://github.com/NVIDIA-AI-IOT/DeepStream_Coding_Agent/issues) | [Discussions](https://github.com/NVIDIA-AI-IOT/DeepStream_Coding_Agent/discussions) | [Contributing](https://github.com/NVIDIA-AI-IOT/DeepStream_Coding_Agent/blob/main/CONTRIBUTING.md) | [Security](https://github.com/NVIDIA-AI-IOT/DeepStream_Coding_Agent/blob/main/SECURITY.md) |
| **Dynamo** | [Issues](https://github.com/ai-dynamo/dynamo/issues) | [Discussions](https://github.com/ai-dynamo/dynamo/discussions) | [Contributing](https://github.com/ai-dynamo/dynamo/blob/main/CONTRIBUTING.md) | [Security](https://github.com/ai-dynamo/dynamo/blob/main/SECURITY.md) |
| **Earth2Studio** | [Issues](https://github.com/NVIDIA/earth2studio/issues) | [Discussions](https://github.com/NVIDIA/earth2studio/discussions) | [Contributing](https://github.com/NVIDIA/earth2studio/blob/main/CONTRIBUTING.md) | [Security](https://github.com/NVIDIA/earth2studio/blob/main/SECURITY.md) |
| **Megatron-Core** | [Issues](https://github.com/NVIDIA/Megatron-LM/issues) | [Discussions](https://github.com/NVIDIA/Megatron-LM/discussions) | [Contributing](https://github.com/NVIDIA/Megatron-LM/blob/main/CONTRIBUTING.md) | [Security](https://github.com/NVIDIA/Megatron-LM/blob/main/SECURITY.md) |
| **NeMo AutoModel** | [Issues](https://github.com/NVIDIA-NeMo/Automodel/issues) | [Discussions](https://github.com/NVIDIA-NeMo/Automodel/discussions) | [Contributing](https://github.com/NVIDIA-NeMo/Automodel/blob/main/CONTRIBUTING.md) | [Security](https://github.com/NVIDIA-NeMo/Automodel/blob/main/SECURITY.md) |
| **NeMo MBridge** | [Issues](https://github.com/NVIDIA-NeMo/Megatron-Bridge/issues) | [Discussions](https://github.com/NVIDIA-NeMo/Megatron-Bridge/discussions) | [Contributing](https://github.com/NVIDIA-NeMo/Megatron-Bridge/blob/main/CONTRIBUTING.md) | [Security](https://github.com/NVIDIA-NeMo/Megatron-Bridge/blob/main/SECURITY.md) |
| **NeMo Platform** | [Issues](https://github.com/NVIDIA-NeMo/nemo-platform/issues) | [Discussions](https://github.com/NVIDIA-NeMo/nemo-platform/discussions) | [Contributing](https://github.com/NVIDIA-NeMo/nemo-platform/blob/main/CONTRIBUTING.md) | [Security](https://github.com/NVIDIA-NeMo/nemo-platform/blob/main/SECURITY.md) |
| **NeMo Retriever** | [Issues](https://github.com/NVIDIA/NeMo-Retriever/issues) | [Discussions](https://github.com/NVIDIA/NeMo-Retriever/discussions) | [Contributing](https://github.com/NVIDIA/NeMo-Retriever/blob/main/CONTRIBUTING.md) | [Security](https://github.com/NVIDIA/NeMo-Retriever/blob/main/SECURITY.md) |
| **NeMo-RL** | [Issues](https://github.com/NVIDIA-NeMo/RL/issues) | [Discussions](https://github.com/NVIDIA-NeMo/RL/discussions) | [Contributing](https://github.com/NVIDIA-NeMo/RL/blob/main/CONTRIBUTING.md) | [Security](https://github.com/NVIDIA-NeMo/RL/blob/main/SECURITY.md) |
| **NemoClaw** | [Issues](https://github.com/NVIDIA/NemoClaw/issues) | [Discussions](https://github.com/NVIDIA/NemoClaw/discussions) | [Contributing](https://github.com/NVIDIA/NemoClaw/blob/main/CONTRIBUTING.md) | [Security](https://github.com/NVIDIA/NemoClaw/blob/main/SECURITY.md) |
| **Nemotron** | [Issues](https://github.com/NVIDIA-NeMo/Nemotron/issues) | [Discussions](https://github.com/NVIDIA-NeMo/Nemotron/discussions) | [Contributing](https://github.com/NVIDIA-NeMo/Nemotron/blob/main/CONTRIBUTING.md) | [Security](https://github.com/NVIDIA-NeMo/Nemotron/blob/main/SECURITY.md) |
| **NVIDIA Digital Health Examples** | [Issues](https://github.com/NVIDIA/digital-health-examples/issues) | [Discussions](https://github.com/NVIDIA/digital-health-examples/discussions) | [Contributing](https://github.com/NVIDIA/digital-health-examples/blob/main/CONTRIBUTING.md) | [Security](https://github.com/NVIDIA/digital-health-examples/blob/main/SECURITY.md) |
| **Physical AI** | — | — | — | — |
| **PhysicsNeMo** | [Issues](https://github.com/NVIDIA/physicsnemo/issues) | [Discussions](https://github.com/NVIDIA/physicsnemo/discussions) | [Contributing](https://github.com/NVIDIA/physicsnemo/blob/main/CONTRIBUTING.md) | [Security](https://github.com/NVIDIA/physicsnemo/blob/main/SECURITY.md) |
| **RAG Blueprint** | [Issues](https://github.com/NVIDIA-AI-Blueprints/rag/issues) | [Discussions](https://github.com/NVIDIA-AI-Blueprints/rag/discussions) | [Contributing](https://github.com/NVIDIA-AI-Blueprints/rag/blob/develop/CONTRIBUTING.md) | [Security](https://github.com/NVIDIA-AI-Blueprints/rag/blob/develop/SECURITY.md) |
| **Skill Card Generator** | [Issues](https://github.com/NVIDIA/Trustworthy-AI/issues) | [Discussions](https://github.com/NVIDIA/Trustworthy-AI/discussions) | [Contributing](https://github.com/NVIDIA/Trustworthy-AI/blob/main/CONTRIBUTING.md) | [Security](https://github.com/NVIDIA/Trustworthy-AI/blob/main/SECURITY.md) |
| **TileGym** | [Issues](https://github.com/NVIDIA/TileGym/issues) | [Discussions](https://github.com/NVIDIA/TileGym/discussions) | [Contributing](https://github.com/NVIDIA/TileGym/blob/main/CONTRIBUTING.md) | [Security](https://github.com/NVIDIA/TileGym/blob/main/SECURITY.md) |
<!-- help-table-end -->

For issues with **this catalog repo itself** (README, structure, listing a new product): [open an issue here](../../issues).

---

## Verifying Skills

Every published skill ships with a detached OMS signature (`skill.oms.sig`). The sync pipeline drops any skill missing the required artifacts before publishing, so every skill in the catalog carries:

- `SKILL.md` — the skill instructions consumed by the agent
- `skill-card.md` — skill identity and governance card
- `skill.oms.sig` — detached OMS signature (verifiable against `nv-agent-root-cert.pem`)
- A Tier-3 evaluation dataset — accepted at `evals/evals.json`, `evals/*.json`, `eval/*.json`, or `benchmark/evals.json`
- `BENCHMARK.md` — generated benchmark report capturing verifiable uplift data

Verify a skill against the NVIDIA trust anchor [`nv-agent-root-cert.pem`](nv-agent-root-cert.pem):

```bash
pip install model-signing
model_signing verify certificate SKILL_DIR \
  --signature SKILL_DIR/skill.oms.sig \
  --certificate_chain nv-agent-root-cert.pem \
  --ignore_unsigned_files
```

A successful verification confirms that the skill contents have not been modified since signing by NVIDIA.

See [Verify Signed Agent Skills](docs/signing-agent-skills.mdx) for signature layout, the trust pipeline, and policy options.

---

## Roadmap

- ✅ Public skills catalog with NVIDIA-verified skills across multiple products
- ✅ Automated sync pipeline with skills mirrored from product repos daily
- ✅ Security scanning for all published skills covering instruction safety and supply-chain integrity
- ✅ Skills signing so every published skill carries a verifiable NVIDIA signature
- ✅ Skills universal evaluation criteria and task-specific criteria
- ✅ Skill Card with machine-readable metadata for identity, provenance, quality, and behavioral boundaries
- 🔲 Compliance gates before external publication
- 🔲 Syndication to external marketplaces and MCP hubs

---

## Repository Structure

```
NVIDIA/skills/
├── skills/                      # 110 verified skills across 24 products,
│   │                              synced from upstream product repos
│   ├── README.md                 # Browser-facing install guidance
│   ├── <product-prefix>-*/       # Flat layout — one dir per skill, product-prefixed
│   │                               # e.g. aiq-*, cuopt-*, cupynumeric-*, dali-*,
│   │                               # deepstream-*, digital-health-*, dynamo-*,
│   │                               # earth2studio-*, mcore-*, nemo-automodel-*,
│   │                               # nemo-data-designer-plugin, nemo-evaluator-plugin,
│   │                               # nemo-mbridge-* (20 skills), nemo-retriever,
│   │                               # nemoclaw-user-* (10 skills), nemotron-*,
│   │                               # physicsnemo-*, rag-*, skill-card-generator,
│   │                               # tilegym-*, accelerated-computing-cudf, cudaq-guide
│   ├── omniverse-*/              # Physical AI — manually staged (see manual-components.yml)
│   ├── physical-ai-*/            # Physical AI — manually staged
│   ├── NeMo-RL/                  # Legacy nested layout (5 skills under one dir)
│   └── video-search-and-summarization/  # Legacy nested layout (15 skills under one dir)
├── components.d/                # Product registry — one file per component, teams onboard here
│   ├── README.md                 # Schema and onboarding instructions
│   └── <product>.yml             # one file per registered product (24 today)
├── plugins/                     # Packaged plugin distributions
│   └── nvidia-skills/            # Curated NVIDIA skills bundle (Claude Code, Codex)
├── plugins.d/                   # Plugin build registry — config for `build-plugins.py`
│   ├── README.md
│   ├── _defaults.yml
│   └── nvidia-skills.yml
├── .claude-plugin/              # Claude Code marketplace metadata
│   └── marketplace.json
├── .agents/plugins/             # Agent marketplace metadata (other clients)
│   └── marketplace.json
├── docs/                        # Long-form documentation (published via Fern)
│   ├── README.md                 # How to build the docs locally
│   ├── index.mdx
│   ├── advanced-install.mdx
│   ├── agent-skill-trust-pipeline.mdx
│   ├── release-checklist.mdx
│   ├── scanning-agent-skills.mdx
│   ├── signing-agent-skills.mdx
│   └── skill-cards.mdx
├── fern/                        # Fern docs site configuration
├── .github/
│   ├── workflows/                # Sync pipeline, plugin validation, DCO check, author verify
│   └── scripts/                  # regenerate-readme.sh, build-plugins.py,
│                                 # manual-components.yml (temp Physical AI catalog
│                                 # exception, removed after Computex 2026),
│                                 # marketplace/metadata.json (skill metadata sidecar)
├── nv-agent-root-cert.pem       # Trust anchor for OMS signature verification
├── skills.sh.json               # Skills.sh marketplace grouping config
├── CHANGELOG.md
├── CONTRIBUTING.md              # Contribution guidelines
├── SECURITY.md                  # Security reporting policy
├── CODE_OF_CONDUCT.md           # Community code of conduct
└── LICENSE                      # Apache 2.0 / CC BY 4.0
```

Skills are maintained in their respective product repos (see the **Source** column in the [Skill Catalog](#skill-catalog)) and synced to this repo daily. Products only appear under `skills/` after the sync pipeline confirms each skill carries:

- `skill.oms.sig` — detached OMS-format signature (verifiable against `nv-agent-root-cert.pem`)
- `skill-card.md` — skill identity and governance card
- A Tier-3 evaluation dataset — accepted at `evals/evals.json`, `evals/*.json`, `eval/*.json`, or `benchmark/evals.json`

When evaluation runs produce a `BENCHMARK.md`, it ships alongside the skill so consumers can see verifiable benchmark uplift data.

---

## Standards & Compatibility

This repository adheres to the [Agent Skills specification](https://agentskills.io/specification):

- Skills are portable directories with a `SKILL.md` file at their root.
- Metadata uses YAML frontmatter with required `name` and `description` fields.
- Skills follow a progressive disclosure model — lightweight metadata loads at startup, full instructions load on activation.
- Validate your skill using the [`skills-ref`](https://github.com/agentskills/agentskills/tree/main/skills-ref) reference library.

---

## License

This project is dual-licensed under the [Apache License 2.0](LICENSE) and [Creative Commons Attribution 4.0 International (CC BY 4.0)](LICENSE).
