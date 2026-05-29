== WHO I AM ==
Name: Pragyan Prayas Jena
Degree: B.Tech CSE, 7th semester, KIIT University, Bhubaneswar
CGPA: ~8.8-8.9 (strong upward trajectory)
Target: MS in Europe — Germany (Freiburg, TUM, Würzburg, 
FAU Erlangen) + Nordics as backup
Focus area for MS: Trustworthy AI / Computational Fairness
Partner/collaborator: Ishuvi Misra (same university, 
working on same internship)

== CURRENT ACTIVE PROJECTS ==
1. DCDD Paper (almost done)
   - Full title: "Disability-Conditioned Demographic Drift 
     in Text-to-Image Models"
   - Target venue: WACV 2026
   - Status: Final stages, data polishing + writing
   - Estimated submission: ~June 10, 2026
   - Used: FLUX.1 [dev], GPT-4o-mini via OpenAI Batch API,
     SigLIP/CLIP embeddings, Chi-Square, Cramér's V, 
     Benjamini-Hochberg FDR, transition matrices
   - Collaborators: Ishuvi (co-implementer), 
     Srikant Panda (Lam Research, mentor), 
     Prof. Lipika Dewangan (KIIT supervisor)

2. NIT Patna Research Internship Paper (NEW — this is 
   what we are finding a topic for)
   - Supervisor: Dr. Krishan Kumar Sethi, NIT Patna
   - Goal: ArXiv preprint + internship certificate
   - Timeline: June 10 → July 31, 2026 (8 weeks)
   - Primary value: Internship certificate for MS apps
   - Stretch goal: Workshop submission

3. Final Year Thesis (not started yet)
   - Begins: Aug-Sep 2026
   - Ends: March 2027

== CONSTRAINTS FOR NIT PATNA PAPER ==
- Budget: MAX ₹5,000 total (save ₹2,000 for Colab Pro)
- GPU: Cloud like google collab or cloud GPU until ~June 20 (MacBook Air M5 24GB arrives)
- After June 20: Apple M5 unified memory, MPS backend
  — good for inference, NOT for training
- Two researchers (me + Ishuvi)
- No extremely expensive APIs
- Must be completable as PILOT STUDY/ journal/ report/ smaller paper in 8 weeks

== DOMAIN KNOWLEDGE / SKILLS WE HAVE ==
- Demographic bias in generative models (DCDD)
- Fairness metrics: Chi-Square, Cramér's V, 
  Benjamini-Hochberg FDR, transition matrices
- Face anonymization literature (read FairDeFace fully)
- NLP bias pipelines (HateBERT, asymmetric loss weights)
- VLM basics: GPT-4o-mini via API, LLaVA architecture
- Python, Flask, FAISS, SQLAlchemy, HuggingFace

== TOPIC SEARCH — WHAT WE'VE DONE SO FAR ==
We ran Gemini Deep Research and verified 10 papers on ArXiv.
All 10 confirmed to exist. The research direction that 
emerged as strongest is:

CANDIDATE TOPIC (Gemini Rank 1):
"Auditing intersectional disability bias in VLMs via 
textual prompt perturbation — does mitigating disability 
bias cause harm to race/gender fairness? 
(Fairness Without Harm paradigm)"

Why this topic:
- Extends DCDD research identity (disability + AI bias)
- CPU/API friendly — no GPU needed
- Open source datasets available (UTKFace, FACET)
- Clear gap: nobody has tested if disability bias 
  mitigation via prompting harms other demographic groups
- Automated evaluation (LLM-as-judge, VADER sentiment)
- Feasible in 8 weeks as pilot study

== PAPERS WE HAVE VERIFIED AND ARE USING ==
All confirmed on ArXiv:
1. VisBias (Huang et al., EMNLP 2025)
2. BiasICL (Xu et al., MICCAI 2025)
3. Glazko et al. FAccT 2024 — disability bias GPT resume
4. Gender Shades (Buolamwini & Gebru, FAccT 2018)
5. Auditing Disability Representation VLMs 
   (Panda et al., arXiv 2026) — Srikant Sir's paper,
   treat as SECONDARY/concurrent, not primary baseline
6. FACET benchmark (Gustafson et al., Meta, 2023)
   ArXiv ID: 2309.00035
7. AccessEval (Panda et al.) — Srikant Sir, secondary
8. Who Gets Left Behind (Dash et al., arXiv 2025)
   — Srikant Sir co-author, secondary

Papers confirmed but not using as baseline:
- debiaSAE, NH-Fair, GLEaN, Edu-MMBias, FairDiffusion,
  FairDeFace (already fully analyzed in prior chat)

== IMPORTANT DECISIONS ALREADY MADE ==
1. NOT doing VLM Sycophancy paper for NIT Patna
   (good idea, saving for thesis or future work)
2. NOT doing Likeness Drift (partner's original idea,
   could revisit later — lost to Disability Bias topic)
3. Srikant Sir's papers = cite as concurrent/related work,
   NOT as primary baseline (conflict of interest risk)
4. ₹2,000 reserved for Colab Pro (compute), 
   NOT for literature tools
5. Using NotebookLM Pro (already have) for PDF analysis
6. Gemini Deep Research for discovery (already done)
7. Topic selection method: limitations section mining
   (researcher's video method — Type 1/2/3 gap framework)

== NOTEBOOKLM STATUS ==
Notebook name: "Internship"
Currently uploaded (5 papers):
- Auditing_disability_representations_in_VLMs.pdf
- BiasICL.pdf
- Glazko_et_al.pdf
- VISBIAS.pdf
- gender_shades.pdf

Still need to upload:
- FACET (ArXiv: 2309.00035)
- One more independent disability+VLM paper 
  NOT from Srikant Sir's group

Next step: Upload remaining papers, then ask 
NotebookLM these 7 questions IN ORDER:

Q1: "What disability categories are tested across 
all papers and which are completely absent?"

Q2: "Which papers test disability bias in visual 
modalities specifically, not just text?"

Q3: "Do any papers test intersectional disability 
bias — meaning disability combined with race AND 
gender simultaneously, not separately?"

Q4: "What datasets do these papers use and what 
are the explicit limitations of those datasets 
mentioned by the authors?"

Q5: "Which future work directions appear in more 
than one paper without any paper in this collection 
having addressed them?"

Q6: "Do any papers test whether prompt interventions 
that reduce disability bias cause harm to other 
demographic groups like race or gender?"

Q7: "What is the most common evaluation metric 
used and what do authors say is missing from 
current evaluation approaches?"

After NotebookLM answers all 7, paste answers 
into new Claude chat for gap classification 
and final problem statement.

== GAP TYPE FRAMEWORK (for Claude to use) ==
Type 1: Gap acknowledged but already being worked on
         by the same authors → skip
Type 2: Gap acknowledged, structurally blocked for 
         original authors but feasible for us → TARGET
Type 3: Gap acknowledged but trivial (just swap dataset) 
         → weak contribution, avoid

== WHAT I NEED FROM NEW CLAUDE CHAT ==
After pasting NotebookLM answers:
1. Classify each gap as Type 1/2/3
2. Check feasibility against our exact constraints
3. Identify strongest novelty claim
4. Draft final one-paragraph problem statement
5. Prepare for Dr. Sethi meeting pitch

== TOOLS AND WORKFLOW ==
Discovery: Gemini Deep Research (done)
Verification: ArXiv manual search (done)  
Deep analysis: NotebookLM Pro (in progress)
Gap evaluation + methodology: Claude
Debugging + iteration: Gemini (high limits)
Compute when needed: Colab Pro (₹1,000/month)

== CLAUDE INTERACTION STYLE ==
- Direct answers, no padding
- Act as intellectual sparring partner
- Push back when reasoning is weak
- Output-first when asked for simple things
- Depth and analytical rigor for research decisions
===========================================