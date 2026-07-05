# OpenSciFlow Position Note v0.1

Status:

```text
Early public feedback draft. Not a mature system evaluation.
```

## One-sentence summary

OpenSciFlow is an early open initiative for describing, validating, and running AI-for-science tools through lightweight plugin manifests, reusable workflow templates, local/HPC execution metadata, and reproducible run records.

## Motivation

AI-for-science projects are producing useful models, agents, workflow tools, and domain packages. The practical bottleneck for many labs is not only model capability. It is also the friction around:

- environment setup;
- local and HPC execution;
- dependency and hardware requirements;
- model-weight provenance;
- input/output expectations;
- license and citation propagation;
- validation tests;
- reproducible reporting;
- clear scientific limitations.

OpenSciFlow focuses on this missing metadata and execution layer.

## What OpenSciFlow proposes

OpenSciFlow starts with three small artifacts:

1. `opensciflow.yaml`: a plugin manifest for scientific tools, models, and scripts.
2. Workflow templates: reviewed task recipes that compose tools into reproducible workflows.
3. Run records: machine-readable logs of inputs, commands, environments, artifacts, citations, and limitations.

The first reference workflow is intentionally narrow:

```text
Protein MD Stability Report Lite
```

It analyzes an existing protein trajectory and reports descriptive metrics such as RMSD, RMSF, radius of gyration, plots, warnings, citations, and reproducibility metadata.

## What OpenSciFlow is not

OpenSciFlow is not:

- a replacement for Nextflow, Snakemake, Galaxy, CWL, AiiDA, Parsl, Slurm, Bioconda, BioContainers, Spack, Apptainer, Hugging Face, BioImage Model Zoo, or domain tools;
- a claim that listed projects are partners;
- a general autonomous scientist;
- a clinical, diagnostic, or drug-development decision system;
- a mature software ecosystem.

## Why we contact upstream projects

When OpenSciFlow lists or drafts metadata for an upstream project, the goal is correction, not endorsement.

Typical questions:

- Is the project classification accurate?
- Are the input/output fields misleading?
- Are licenses, citations, model weights, and data boundaries represented correctly?
- What should a workflow runner validate before execution?
- Which safety or scientific limitations should be shown to users?

Maintainers can respond with a short correction comment. No integration work is expected.

## Current public entry points

- Organization: https://github.com/OpenSciFlow
- Landscape map: https://github.com/OpenSciFlow/awesome-ai4s-workflows
- Plugin manifest draft: https://github.com/OpenSciFlow/plugin-manifest
- Workflow templates: https://github.com/OpenSciFlow/workflow-templates
- Reference prototype: https://github.com/OpenSciFlow/biopilot-prototype
- Community process: https://github.com/OpenSciFlow/community

## Immediate feedback requested

OpenSciFlow is currently seeking feedback on:

- required vs optional manifest fields;
- model-weight and data provenance;
- citation and license propagation;
- local/HPC execution metadata;
- validation levels from schema check to smoke test;
- safe boundaries for agent-triggered scientific workflows;
- first protein-computing workflow design.

## Claim boundary

OpenSciFlow should be evaluated first as a metadata and workflow-convention proposal. It should not be presented as evidence that AI agents can autonomously perform reliable science, nor as a benchmark result for any scientific model.
