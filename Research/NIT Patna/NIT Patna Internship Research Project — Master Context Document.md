## Project Status

Research internship under Dr. Krishan Kumar Sethi (NIT Patna).

Current project direction:

**Probing Moral-Body Conflation in Text-to-Image Models**

Primary inspiration:  
Warren et al. (NAACL 2025) — "Decoding Fatphobia: Anti-Fat and Pro-Thin Bias in AI-Generated Images"

Current draft proposal investigates whether modern open-weight text-to-image models associate moral virtue and moral failure with specific body types.

---

# Important Context

This project is NOT being treated as a serious publication-first research effort.

The primary objective is:

1. Successfully complete the NIT Patna internship.
    
2. Produce a technically defensible report/paper.
    
3. Obtain internship certification and CV value.
    
4. Learn proper research workflow and habits.
    

The project is constrained by:

- Approximately 20–30 days remaining.
    
- Approximately 3–4 hours available per day.
    
- Minimal supervisor interaction.
    
- Small research team (Pragyan + Ishuvi).
    

Because of these constraints, scope reduction is considered a feature, not a failure.

---

# Research Philosophy Going Forward

A major lesson from previous DCDD work and earlier research experiences is that the team does not want to continue:

- undocumented experimentation
    
- unclear methodology
    
- ad hoc paper writing
    
- results without provenance
    
- changing hypotheses after seeing outputs
    
- scattered files and notebooks
    

The goal is to gradually learn more rigorous research practices while still delivering the internship project.

This internship paper is intentionally treated as a transition project:

"Finish efficiently, but build habits that can scale to future serious research."

---

# Current Strategic Decision

The original PPT proposes:

Study 1:  
Weight Bias Replication

Study 2:  
Age Bias

Study 3:  
Composite Body Analysis

This scope is too large for the available time.

Current plan:

## Core Study

Replicate Warren et al. using open-weight models.

Research Question:

Does the fatphobia effect observed in DALL-E 3 also appear in open-weight models?

Models:

- FLUX.1-dev
    
- SDXL
    

SD3.5 currently excluded unless time remains.

---

## Small Extension

If the core study succeeds:

Investigate age bias using the same generated image dataset.

No additional image generation.

No additional data collection.

Simply run age annotation on existing images.

This becomes the project's novel extension.

---

# Things We Are Explicitly NOT Doing

For this internship project:

- No massive benchmark creation
    
- No complex fairness frameworks
    
- No multiple VLM judge systems
    
- No large-scale inter-rater reliability studies
    
- No extensive human annotation campaigns
    
- No ambitious three-study publication agenda
    

The objective is completion and learning.

---

# Research Workflow

Every project should follow:

Question  
↓  
Baseline  
↓  
Data Collection  
↓  
Measurement  
↓  
Analysis  
↓  
Writing

Paper writing must happen after evidence exists.

Writing is not research.

Writing documents research.

---

# Folder Structure

fatphobia-audit/

├── docs/  
├── literature/  
├── datasets/  
├── code/  
├── experiments/  
├── results/  
├── figures/  
├── paper/  
├── meeting-notes/  
└── project-log/

---

# Literature Structure

literature/

├── papers/  
├── summaries/  
├── gap-analysis/  
└── bibliography/

Paper summaries should contain:

- Problem
    
- Method
    
- Dataset
    
- Metrics
    
- Limitations
    
- Possible Extensions
    

Nothing more.

---

# Code Structure

code/

├── generation/  
├── annotation/  
├── analysis/  
└── visualization/

Example:

generation/  
generate_flux.py

annotation/  
weight_labeling.py

analysis/  
weight_statistics.py

visualization/  
distribution_plots.py

---

# Data Provenance Rules

Every image must be traceable.

Metadata should record:

- image_id
    
- prompt
    
- model
    
- seed
    
- timestamp
    

Stored in metadata.csv

No manually renamed files.

No undocumented outputs.

---

# Experiment Registry

Every experiment receives an ID.

Example:

EXP-001  
Warren Replication Pilot

EXP-002  
Annotation Validation

EXP-003  
Age Bias Extension

Every experiment must contain:

Question

Hypothesis

Method

Results

Decision

Even failed experiments remain documented.

---

# Research Log

Maintain a daily log.

Example:

Date:  
2026-06-24

Work Completed:  
Generated pilot images.

Issue:  
Weak signal in FLUX outputs.

Decision:  
Increase diversity settings.

Next Step:  
Run second pilot.

The log exists to prevent future confusion during paper writing.

---

# 30-Day Execution Plan

## Week 1

Infrastructure

Goals:

- Finalize folder structure.
    
- Obtain Warren prompt list.
    
- Build generation pipeline.
    
- Build annotation pipeline.
    
- Create experiment registry.
    

Deliverable:

Working repository.

No large experiments yet.

---

## Week 2

Data Generation

Generate:

20 prompts  
× 50 images  
× 2 models

Total:

Approximately 2,000 images.

Deliverables:

- Generated dataset
    
- Metadata records
    
- Organized storage
    

---

## Week 3

Weight Bias Analysis

Run automated annotation.

Generate:

- Weight labels
    
- Distributions
    
- Statistical tests
    
- Initial figures
    

Deliverable:

Core study completed.

At this point the internship already has a defensible result.

---

## Week 4

Age Bias Extension

Reuse the same image dataset.

Run age classification.

Generate:

- Age distributions
    
- Comparative analysis
    
- Additional figures
    

Deliverable:

Novel extension beyond Warren.

---

# Success Criteria

Minimum Success:

- Complete dataset
    
- Complete analysis
    
- Technical report
    
- Internship certificate
    

Good Success:

- Weight replication across open models
    
- Age extension completed
    
- Clean repository and documentation
    

Excellent Success:

- Submission-ready manuscript
    
- Reproducible codebase
    
- Foundation for future fairness research
    

---

# Long-Term Goal

This project is not intended to become the team's definitive research contribution.

Instead, it serves as a bridge between:

Old style research:  
"Do experiments somehow and write later."

and

Future style research:  
"Build reproducible systems, document decisions, preserve evidence, and write from recorded results."

The internship certificate is the immediate outcome.

Learning a repeatable research workflow is the lasting outcome.

**Whenever we start a new chat, paste three things:**

1. This master context document.
2. Latest PPT / proposal version.
3. A short status update:
	Current date:
	Completed:
	Blocked on:
	Next objective:
