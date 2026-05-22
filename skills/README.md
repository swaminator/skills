<!-- SPDX-License-Identifier: Apache-2.0 AND CC-BY-4.0 -->
<!-- Copyright (c) 2026 NVIDIA Corporation. All rights reserved. -->

# NVIDIA Skills Taxonomy Implementation Guidance

This README defines the recommended skills taxonomy, customer-facing subdomain descriptions, naming guidance, and validation expectations for the `skills/` catalog.

The catalog features verified skills with completed evaluations. To verify a featured skill, look for the `*.oms.sig` signature file in the skill folder and open its `evals.json` file to review the completed evaluation coverage.

No skill currently has both files, so this directory intentionally contains subdomain folders but no product skill folders yet. When skills satisfy both gates, those skill folders should be retained in the appropriate subdomain and all other skill folders should remain out of the catalog.

## Goals

- Organize skills around customer-facing subdomains that are specific enough to help users browse the catalog.
- Show product- or workflow-first skill-name examples, followed by the action or outcome the skill supports.
- Make clear that final `SKILL.md` frontmatter names should come from the owning product or skill team.
- Keep domain/category context out of the `SKILL.md` frontmatter `name` unless the owning team determines it is part of the product or workflow name.
- Preserve compatibility with existing repo automation, catalog generation, README generation, and skill-discovery behavior.

## Skill Owner Naming Ownership

Skill names shown in taxonomy planning are examples, not final rename decisions. They illustrate the requested product- or workflow-first naming pattern and provide a starting point for owner review. Final `SKILL.md` frontmatter `name` values should be proposed or confirmed by the skill owners before any repo changes are made.

## Active Subdomain Folders

This directory currently includes folders for subdomains with more than one current skill:

- `training-ai`
- `agentic-ai`
- `inference-ai`
- `decision-optimization`
- `vision-ai`
- `gpu-development`

## Subdomain Catalog

Use these descriptions as customer-facing copy below each subdomain name in catalog UI, README, or repo browsing surfaces. Each description leads with no more than four core task verbs.

| Subdomain | Repo slug | Current skill count | Customer-facing description |
|---|---|---:|---|
| Training AI | `training-ai` | 41 | Build, validate, tune, and maintain large-scale model training workflows, including distributed training, model support, training validation, performance tuning, and training-stack CI. |
| Agentic AI | `agentic-ai` | 33 | Build and operate agentic systems, including RAG workflows, evaluation harnesses, tool use, policy, sandboxing, agent configuration, and agent workflow automation. |
| Inference AI | `inference-ai` | 29 | Deploy, serve, optimize, and evaluate models for production inference, including quantization, runtime performance, and serving configuration. |
| Decision Optimization | `decision-optimization` | 12 | Formulate and solve routing, scheduling, and numerical optimization problems using optimization solvers, APIs, services, and deployment workflows. |
| Vision AI | `vision-ai` | 12 | Build vision and video AI workflows for analytics, search, summarization, alerts, real-time understanding, and model integration. |
| GPU Development | `gpu-development` | 10 | Develop, tune, profile, and integrate GPU kernels and accelerated code, including CUDA-adjacent workflows, autotuning, low-level performance work, and framework integration. |
| Conversational AI | `conversational-ai` | 1 | Build and deploy speech, voice, dialogue, and multimodal conversational AI workflows, including real-time assistant and voice-agent experiences. |
| Quantum Computing | `quantum-computing` | 1 | Build, run, and validate quantum and hybrid quantum-classical applications, including CUDA-Q development workflows. |
| AI Factory | `ai-factory` | 0 | Design, deploy, operate, and optimize infrastructure and workflows for producing, serving, and managing AI systems at scale. |
| AI Storage | `ai-storage` | 0 | Plan and operate storage, data movement, and data-access workflows for AI training, inference, evaluation, and production workloads. |
| AV Simulation | `av-simulation` | 0 | Build and run autonomous-vehicle simulation workflows for scenario generation, validation, replay, and autonomy testing. |
| Cybersecurity | `cybersecurity` | 0 | Secure systems, detect threats, analyze vulnerabilities, and support secure AI and infrastructure workflows. |
| Data Science | `data-science` | 0 | Prepare, analyze, explore, and model data for AI and accelerated analytics workflows that are not specific to one training, inference, or agent task. |
| Digital Twins | `digital-twins` | 0 | Build, simulate, connect, and operate digital representations of physical systems, environments, factories, and assets. |
| Extended Reality | `extended-reality` | 0 | Build immersive augmented, virtual, and mixed-reality workflows for visualization, simulation, and interactive experiences. |
| Gaming | `gaming` | 0 | Build, optimize, and test game development workflows, game technologies, rendering pipelines, and player-facing interactive experiences. |
| GPU Virtualization | `gpu-virtualization` | 0 | Deploy, configure, monitor, and troubleshoot virtual GPU environments, GPU sharing, and virtualized accelerated workloads. |
| Infrastructure | `infrastructure` | 0 | Deploy, operate, monitor, and troubleshoot clusters, runtimes, services, networking, and platform infrastructure for accelerated and AI workloads. |
| In-Vehicle Computing | `in-vehicle-computing` | 0 | Develop, deploy, and validate software workflows for vehicle compute platforms, in-cabin systems, and automotive edge runtime environments. |
| Networking | `networking` | 0 | Configure, operate, optimize, and troubleshoot networking workflows for data centers, clusters, edge systems, and accelerated infrastructure. |
| Physical AI | `physical-ai` | 0 | Build and validate AI workflows that interact with the physical world, including robotics, autonomy, simulation, synthetic data, and embodied AI systems. |
| Robotics | `robotics` | 0 | Build, deploy, test, and operate robotic systems, robot policies, robot applications, and robot development workflows. |
| Robotics Simulation | `robotics-simulation` | 0 | Build and run robotics simulation workflows for training, testing, validation, synthetic data generation, and scenario coverage. |
| Scientific Visualization | `scientific-visualization` | 0 | Visualize, inspect, and communicate scientific and engineering data, simulations, models, and computational results. |
| Simulation and Modeling | `simulation-modeling` | 0 | Create, run, validate, and analyze simulation and modeling workflows for systems, environments, processes, and physical phenomena. |

## General Implementation Guidance

- Treat this as a taxonomy and naming recommendation, not a required file-move recipe.
- Decide whether subdomain grouping should be represented through physical folders, catalog metadata, generated README sections, or a hybrid of those approaches.
- Prefer the implementation that creates the least disruption to existing sync workflows, source-repo mirroring, generated documentation, and skill discovery.
- Keep the source of truth clear. If subdomains live in `components.d`, metadata, generated catalog data, or another config surface, document that choice in the PR.
- Preserve stable product/component identity even if the browsing surface changes. Product names still matter for search, collisions, and user recognition.
- Avoid encoding the subdomain into each skill name. The skill `name` should remain product- or workflow-first unless a skill owner has a product-specific reason to do otherwise.
- Validate nested paths or metadata-driven grouping against the actual tools that install, sync, discover, and display skills.

## Implementation Decisions To Resolve

| Decision | Guidance |
|---|---|
| Physical folders vs metadata | Use physical folders only if the sync and discovery tooling can support the resulting layout cleanly. Metadata or generated catalog grouping may be safer if the current tooling expects component-level folders. |
| Component-level vs skill-level assignment | Most components map cleanly to one subdomain. TensorRT-LLM has both inference and GPU-kernel skills, so the implementer should decide whether to support skill-level assignment or keep the component together and expose secondary grouping in metadata. |
| Backward compatibility | Check whether existing links, install paths, docs, or generated README tables assume the current flat component layout. Add redirects, aliases, or migration notes if needed. |
| `components.d` role | If `components.d` remains the source of truth, update it in the smallest way that supports subdomain grouping without making onboarding harder for product teams. |
| Customer-facing descriptions | Store descriptions somewhere maintainable so the catalog and README can reuse the same copy instead of duplicating it manually. |
| Validation | Run the repo's normal validation and add targeted checks for total skill count, duplicate names, legacy prefixes, and catalog link integrity. |

## Component Classification Guidance

This table shows the recommended subdomain classification by current component. It is meant to guide implementation, not prescribe a specific file path or config schema.

| Component | Recommended subdomain classification | Current skill count | Notes |
|---|---|---:|---|
| `CUDA-Q` | Quantum Computing (`quantum-computing`) | 1 | Component maps cleanly to one subdomain. |
| `cuopt` | Decision Optimization (`decision-optimization`) | 12 | Component maps cleanly to one subdomain. |
| `DALI` | Inference AI (`inference-ai`) | 1 | Component maps cleanly to one subdomain. |
| `deepstream` | Vision AI (`vision-ai`) | 2 | Component maps cleanly to one subdomain. |
| `Megatron-Bridge` | Training AI (`training-ai`) | 29 | Component maps cleanly to one subdomain. |
| `Megatron-Core` | Training AI (`training-ai`) | 12 | Component maps cleanly to one subdomain. |
| `Model-Optimizer` | Inference AI (`inference-ai`) | 8 | Component maps cleanly to one subdomain. |
| `NeMo-Evaluator` | Agentic AI (`agentic-ai`) | 1 | Component maps cleanly to one subdomain. |
| `NeMo-Evaluator-Launcher` | Agentic AI (`agentic-ai`) | 3 | Component maps cleanly to one subdomain. |
| `NeMo-Gym` | Agentic AI (`agentic-ai`) | 5 | Component maps cleanly to one subdomain. |
| `NemoClaw` | Agentic AI (`agentic-ai`) | 23 | Component maps cleanly to one subdomain. |
| `nemotron-voice-agent` | Conversational AI (`conversational-ai`) | 1 | Component maps cleanly to one subdomain. |
| `rag` | Agentic AI (`agentic-ai`) | 1 | Component maps cleanly to one subdomain. |
| `TensorRT-LLM` | GPU Development (`gpu-development`): 3; Inference AI (`inference-ai`): 20 | 23 | Component spans more than one subdomain; choose a component-level or skill-level grouping strategy during implementation. |
| `TileGym` | GPU Development (`gpu-development`) | 7 | Component maps cleanly to one subdomain. |
| `video-search-and-summarization` | Vision AI (`vision-ai`) | 10 | Component maps cleanly to one subdomain. |

## Validation Expectations

| Check | Expected result |
|---|---:|
| Current `SKILL.md` files represented | 139 |
| Duplicate example `name` values | 0 |
| Example `name` values over 64 characters | 0 |
| Example `name` values using legacy domain prefixes | 0 |
| Example names not in the 2026-05-19 reviewed naming list | 6 |

Before merging an implementation PR, verify that:

- Skill discovery still finds the expected set of current skills.
- Generated README and catalog links resolve correctly.
- Install workflows still work for users installing individual skills and broader NVIDIA skill sets.
- Final owner-approved `SKILL.md` frontmatter `name` values do not start with `ai-ml-`, `physical-ai-`, `accelerated-computing-`, `infrastructure-`, or `graphics-media-`.
- Customer-facing catalog output shows the approved subdomain display names and kebab-case repo slugs.
- Any implementation-specific tradeoffs, especially around mixed-subdomain components, are documented in the PR.

## Skill Owner Review Notes

All final skill names should come from the skill owners. These examples were not part of the 2026-05-19 reviewed naming list, so they should receive an extra owner check before they are used as rename candidates.

| Component | Skill folder | Example `name` | Recommended subdomain |
|---|---|---|---|
| `DALI` | `dali-dynamic-mode` | `dali-use-dynamic-mode` | Inference AI |
| `Megatron-Bridge` | `nemo-rl-e2e-testing` | `megatron-bridge-test-nemo-rl-e2e` | Training AI |
| `Megatron-Bridge` | `verl-e2e-testing` | `megatron-bridge-test-verl-e2e` | Training AI |
| `NeMo-Gym` | `nemo-gym-debugging` | `nemo-gym-debug-runs` | Agentic AI |
| `NeMo-Gym` | `nemo-gym-pivot-datasets` | `nemo-gym-create-pivot-datasets` | Agentic AI |
| `NeMo-Gym` | `nemo-gym-reward-profiling` | `nemo-gym-profile-rewards` | Agentic AI |
