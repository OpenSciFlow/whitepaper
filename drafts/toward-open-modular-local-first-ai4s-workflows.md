# Toward Open, Modular, and Local-First AI for Science Workflows

## Status

Draft 0.2 working draft for community feedback. This is a position paper draft, not a mature system evaluation.

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

## 1. Introduction draft

AI for Science is entering a phase in which useful capabilities are no longer concentrated in a single kind of artifact. Research groups now encounter foundation models, specialized scientific models, agent interfaces, domain packages, workflow engines, model hubs, container registries, and high-performance computing systems in the same practical workflow. A protein researcher may need a molecular dynamics tool, a trajectory-analysis library, a local report generator, a citation trail, and a cluster scheduler. A chemistry researcher may need a docking model, molecule preprocessing, model weights, GPU-aware execution, and clear warnings about what a confidence score does and does not mean. In both cases, scientific value depends not only on model quality, but on whether the surrounding execution and provenance layer is explicit enough to be inspected, reproduced, and corrected.

Natural-language interfaces can reduce the friction of starting a task, but they do not remove the need for structured execution. A language model can help a researcher ask for "trajectory stability analysis" or "dock this ligand to this protein", yet the system still needs to know which tool is allowed to run, which inputs are required, which environment is expected, whether a GPU is needed, which model weights may be downloaded, what files should be produced, what citation should be attached, and which scientific claims are outside the tool's scope. Without this metadata, agent-driven scientific workflows risk becoming convenient wrappers around opaque commands.

Existing scientific workflow systems already solve important parts of this problem. Systems such as Nextflow, Snakemake, Galaxy, CWL, AiiDA, Parsl, and HPC schedulers provide mature patterns for orchestration, provenance, and scale. Package and container ecosystems such as Conda, Bioconda, BioContainers, Spack, Docker, and Apptainer address installation and portability. Domain libraries such as MDAnalysis, OpenMM, GROMACS, BioBB, BioSimSpace, RDKit, and many others encode deep scientific practice. OpenSciFlow is not proposed as a replacement for these systems. Its narrower goal is to define a lightweight, correction-friendly layer that helps agents, workflow templates, and local/HPC runners understand the metadata needed to use such tools responsibly.

The central proposal is simple: before an AI-for-science system executes a scientific tool, it should be able to read a small manifest that describes the tool's inputs, outputs, environment, hardware, model weights, validation checks, licenses, citations, limitations, and safe execution modes. Before a user trusts a multi-step task, they should be able to inspect a workflow template that states what will run and what artifacts will be produced. After execution, the system should produce a run record that captures inputs, commands, versions, logs, artifacts, citations, and warnings. OpenSciFlow starts by drafting these artifacts for a narrow reference use case rather than claiming a universal platform.

## 2. Problem statement draft

The first problem is tool and model fragmentation. AI-for-science tools often expose different assumptions about inputs, model weights, runtime environments, and outputs. Some tools are Python packages, some are command-line programs, some are notebooks, some are containerized services, and some are hosted demos. A researcher or agent that wants to compose them into a workflow must translate between these conventions manually. This makes reuse fragile and makes it hard for a downstream system to know which assumptions are safe.

The second problem is environment ambiguity. Many scientific tools depend on specific Python versions, compiled libraries, CUDA versions, GPU availability, external binaries, or HPC site policies. A natural-language interface that hides these constraints can make the user experience smoother, but it can also obscure the true execution risk. A workflow metadata layer should expose environment options explicitly: local Conda, Docker, Apptainer, system install, or Slurm execution. It should also distinguish between "available", "missing", "partial", and "unsupported" rather than silently trying arbitrary installation commands.

The third problem is provenance loss. In a research workflow, the output file is not enough. The user needs to know what input files were used, which hashes they had, which command ran, which versions were active, which model weights were loaded, which logs were produced, and which citations and limitations belong with the result. This is especially important when AI models or agents are involved, because the temptation to present a polished report can hide fragile execution details.

The fourth problem is credit and license propagation. Scientific tools and datasets come with authorship, citation, and licensing obligations. Model weights and example datasets may have terms that differ from the surrounding code. If an agent or workflow runner downloads, runs, or reports on these artifacts without preserving credit and license metadata, it creates both ethical and practical barriers to adoption. A manifest should make these fields visible before execution, not after publication.

The fifth problem is scientific overclaiming. Many computational outputs are descriptive, approximate, or hypothesis-generating. A molecular dynamics stability report does not prove biological function. A docking pose does not prove binding affinity, drug efficacy, or clinical relevance. A model confidence score is not automatically a validated scientific conclusion. OpenSciFlow therefore treats limitations and safety notes as first-class metadata, not as optional prose at the end of a report.

The final problem is correction and governance. Early ecosystem maps can easily misclassify projects, use stale links, miss citations, or imply relationships that do not exist. OpenSciFlow's public outreach should therefore be correction-oriented: listed projects are related references, not partners unless maintainers explicitly agree. The initiative should be judged by how quickly it accepts corrections and removes misleading claims.

## Remaining structure

### 1. Introduction

Drafted above.

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

Drafted above.

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
