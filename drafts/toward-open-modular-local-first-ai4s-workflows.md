# Toward Open, Modular, and Local-First AI for Science Workflows

## Status

Draft 0.1 outline for community feedback. This is a position paper draft, not a mature system evaluation.

## Abstract draft

AI for Science is producing a rapidly growing set of models, tools, and agent systems across biology, chemistry, materials science, and scientific computing. However, practical adoption in research labs remains constrained by fragmented environments, unclear dependency requirements, heterogeneous local/HPC infrastructure, weak provenance capture, and limited interoperability between models and workflow engines.

We argue that the central bottleneck is not only model capability, but the absence of open, lightweight conventions for describing scientific tools, execution environments, workflow templates, validation tests, citations, limitations, and reproducibility records.

We propose OpenSciFlow, an early open initiative for modular, local-first, and HPC-ready AI for Science workflows. The first design artifact is a plugin manifest, `opensciflow.yaml`, paired with reusable workflow templates and a reference protein-computing demonstration. Rather than replacing workflow engines or domain tools, OpenSciFlow aims to make existing tools discoverable and executable through explicit metadata and reproducible run records.

## Thesis

Natural-language agents can become a convenient entry point for scientific computing tasks, but the durable value is in:

- plugin metadata;
- workflow templates;
- controlled local/HPC execution;
- validation tests;
- license and citation propagation;
- reproducibility records;
- explicit limitations.

## Proposed structure

### 1. Introduction

- AI for Science models and agents are growing quickly.
- Real lab adoption is blocked by execution, environment, and reproducibility friction.
- Natural-language interfaces are useful but insufficient.
- Open infrastructure is needed between models, tools, workflows, and local/HPC systems.

### 2. Landscape

Cover:

- AI for Science agents;
- scientific workflow systems;
- model hubs and model zoos;
- package/container systems;
- HPC schedulers;
- reproducibility and provenance tools;
- protein, chemistry, and materials workflows.

### 3. Problem statement

Key problems:

- model islands;
- environment setup friction;
- dependency and hardware ambiguity;
- HPC deployment heterogeneity;
- weak provenance capture;
- unclear license/citation propagation;
- AI hallucination risk in scientific workflows.

### 4. Design principles

- Open by default.
- Local-first.
- Interoperable with existing tools.
- Minimal but explicit metadata.
- Human approval for install/execution.
- Credit-preserving.
- Limitation-aware.

### 5. OpenSciFlow plugin manifest

Introduce `opensciflow.yaml`:

- inputs/outputs;
- environment;
- hardware;
- model weights;
- execution commands;
- Slurm support;
- validation tests;
- safety notes;
- license/citation;
- known limitations.

### 6. Workflow templates

Explain how workflow templates compose plugins:

- task description;
- ordered steps;
- DAG dependencies;
- required/optional tools;
- fallback tools;
- estimated runtime;
- reproducibility metadata;
- report templates.

### 7. Reference use case: protein MD stability

Use an existing trajectory to produce:

- RMSD;
- RMSF;
- radius of gyration;
- plots;
- report;
- run manifest.

Clarify that this demo proves workflow execution and reproducibility capture, not biological truth or drug efficacy.

### 8. Relation to existing systems

OpenSciFlow should complement, not replace:

- Nextflow;
- Snakemake;
- Galaxy;
- CWL;
- AiiDA;
- Parsl;
- Bioconda;
- BioContainers;
- Spack;
- Apptainer;
- Hugging Face Hub;
- BioImage Model Zoo;
- GROMACS;
- OpenMM;
- MDAnalysis;
- BioBB;
- BioSimSpace.

### 9. Governance and community

Discuss:

- related-project correction policy;
- manifest ownership;
- contributor roles;
- authorship policy;
- avoiding false partnership claims.

### 10. Risks and open problems

Cover:

- security of local command execution;
- license ambiguity;
- scientific validity;
- HPC site heterogeneity;
- weak adoption risk;
- large-company competition;
- maintenance burden.

### 11. Conclusion

Call for community feedback on:

- manifest fields;
- workflow template fields;
- reproducibility metadata;
- first protein-computing reference workflow.

## Planned figures

1. Ecosystem landscape map.
2. OpenSciFlow architecture diagram.
3. `opensciflow.yaml` manifest anatomy.
4. Protein MD stability workflow DAG.
5. Comparison table: model hubs, workflow engines, commercial AI workbenches, OpenSciFlow.

## Candidate venues

- NeurIPS AI for Science workshops.
- ICML AI for Science workshops.
- ICLR scientific discovery / agents workshops.
- WORKS workshop.
- IEEE eScience.
- SC workflow/HPC workshops.
- ISMB / BOSC.
- JOSS later, only after there is mature software.

