## 1. Is Working on This a Smart Move? (The Citation Concern)

The low citation count (4 citations) is **not a red flag — it's actually expected and here's why:**

The paper was published at **NAACL 2025** — that's April 2026, roughly **one month ago**. Academic citation cycles take 6–18 months minimum. A paper published one month ago having 4 citations is actually _above average_ for its age. Compare: Bianchi et al. (FAccT 2023) now has hundreds of citations — but in its first month it had zero.

More importantly, citation count of the anchor paper is the **wrong metric** for evaluating your project. The right questions are:

**Does a real gap exist?** Yes — confirmed. No paper has replicated Warren across open-weight models. No paper has used moral probing for age bias. These are real, verifiable absences.

**Is the venue credible?** Yes — NAACL Findings is a legitimate, peer-reviewed ACL venue. It passed peer review. A reviewer already accepted the methodology. You're building on a reviewed foundation, not a preprint.

**Is the methodology sound enough to build on?** Yes — the moral probing framework is theoretically grounded, the measurement instrument is medically validated, and it's reproducible (they open-sourced code and data).

**Is your output goal realistic?** Your goal is an **ArXiv preprint + internship certificate**. You are not targeting NAACL yourself. For ArXiv, the bar is: novel, coherent, methodologically sound. You clear that bar comfortably.

**The real risk isn't citation count.** The real risk is: does GPT-4o-mini reliably annotate weight and age categories from FLUX-generated images? That's your actual go/no-go checkpoint — and it costs maybe ₹200 to test on 50 images before committing.

**Verdict:** Proceed. The concern is rational but misdirected. Low citations on a one-month-old paper means nothing. The gap is real, the methodology is borrowed from peer-reviewed work, and your output target is ArXiv — not a top conference.

---

## 2. All Papers to Upload to NotebookLM

Find and verify each on Semantic Scholar or Google Scholar before uploading. Organized by notebook.

### Notebook A — Methodology Papers

These inform _how_ you design your pipeline.

1. **Warren et al. (2025)** — "Decoding Fatphobia: Examining Anti-Fat and Pro-Thin Bias in AI-Generated Images" — NAACL 2025 _(you have the PDF already)_
2. **Luccioni et al. (2023)** — "Stable Bias: Evaluating Societal Representations in Diffusion Models" — NeurIPS 2023 — arXiv:2303.11408
3. **Bianchi et al. (2023)** — "Easily Accessible Text-to-Image Generation Amplifies Demographic Stereotypes at Large Scale" — FAccT 2023 — find on ACM Digital Library
4. **Jha et al. (2024)** — "ViSAGe: A Global-Scale Analysis of Visual Stereotypes in Text-to-Image Generation" — ACL 2024 — arXiv:2401.06310
5. **Vandewiele et al. (2025)** — "Beyond the Prompt: Gender Bias in Text-to-Image Models, with a Case Study on Hospital Professions" — arXiv:2510.00045
6. **Cho et al. (2023)** — "DALLEval: Probing the Reasoning Skills and Social Biases of Text-to-Image Generation Models" — ICCV 2023 — arXiv:2202.04053

### Notebook B — Domain and Gap Papers

These inform _what_ you're studying and _where_ your contribution sits.

1. **Warren et al. (2025)** — same paper, upload to both notebooks
2. **Tian et al. (2026)** — "Investigating Disability Representations in Text-to-Image Models" — arXiv (Yang Tian, Yu Fan, Liudmila Zavolokina, Sarah Ebling) — find on arXiv
3. **Mack et al. (2024)** — "'They only care to show us the wheelchair': Disability Representation in Text-to-Image AI Models" — CHI 2024 — find on ACM Digital Library
4. **Porikli & Porikli (2025)** — "Hidden Bias in the Machine: Stereotypes in Text-to-Image Models" — CVPR EMACS Workshop 2025 — arXiv:2506.13780
5. **Wilson et al. (2025)** — "Bias Amplification in Stable Diffusion's Representation of Stigma Through Skin Tones and Their Homogeneity" — AIES 2025 — arXiv:2508.17465
6. **Ertman et al. (2025)** — "Disability portrayals in artificial intelligence text-to-image generation: Influence of context and the medicalization of disability" — Rehabilitation Psychology 2025 — find on PubMed or Google Scholar

---

## 3. All Questions to Ask NotebookLM

### Notebook A — Methodology Questions

Ask these one at a time, not all together:

**Q1 (Pipeline design):**

> "Across all papers in this notebook, what are the documented limitations of manual human annotation for measuring body-related bias in T2I models? Which papers propose automated alternatives, and what validation steps did they use to ensure automated annotation was reliable?"

**Q2 (VLM annotation):**

> "Which papers in this notebook use Vision-Language Models (like GPT-4V, LLaVA, or GPT-4o) to annotate or classify generated images? What prompting strategies did they use, and what were the known failure modes or hallucination risks they identified?"

**Q3 (Multi-model comparison):**

> "What methodological choices did papers make when comparing bias across multiple T2I models — specifically around sample size, prompt standardization, and statistical tests? What sample sizes were considered sufficient for Chi-Square or similar tests?"

**Q4 (Moral probing specifically):**

> "Which papers use morally-valenced or sentiment-polarized prompts to probe T2I models for bias, rather than explicit demographic descriptors? What theoretical justification do they give for this indirect probing approach?"

**Q5 (Statistical methods):**

> "What statistical tests are used across these papers to measure bias in generated image distributions — Chi-Square, Cramér's V, t-tests, effect sizes? What thresholds or corrections (like Benjamini-Hochberg FDR) are applied for multiple comparisons?"

---

### Notebook B — Gap and Domain Questions

**Q1 (Age bias gap):**

> "Is there any paper in this notebook that specifically studies age bias or ageism in text-to-image models using moral or sentiment-based prompting? If not, what do the papers collectively suggest about age as an understudied dimension?"

**Q2 (Weight bias gap):**

> "Beyond Warren et al., do any papers in this notebook study body weight or body size bias in T2I models specifically? What do they collectively say about the state of body diversity representation in generative AI?"

**Q3 (Moral conflation):**

> "Do any papers discuss the theoretical mechanism by which T2I models associate non-normative physical characteristics with negative moral or social attributes? What frameworks — semiotic, co-occurrence-based, or otherwise — do they use to explain this?"

**Q4 (Methodological gaps):**

> "Based on all papers in this notebook, what are the three most significant methodological gaps in how T2I bias is currently studied — specifically regarding physical body characteristics beyond race and gender?"

**Q5 (Your novelty check):**

> "Has any paper in this notebook studied the intersection of body weight bias AND age bias in the same T2I audit study? Has any paper applied moral probing to age as a variable? What would be needed to make such a study credible?"

---

## 4. Full Framework — What to Do With NotebookLM Findings

Follow this exactly, step by step.

---

### Phase 1 — NotebookLM Session (Day 1–2)

**Step 1:** Upload papers to both notebooks as listed above. Verify each paper actually loaded correctly by asking: _"List all papers currently in this notebook with their venue and year."_ If a paper didn't load, its content won't appear.

**Step 2:** Ask all Notebook A questions first. Copy every response into a document. Don't interpret yet — just collect.

**Step 3:** Ask all Notebook B questions. Same — collect verbatim.

**Step 4:** Look for contradictions between what NotebookLM says and what Gemini said earlier. If NotebookLM says a methodology has a known failure mode that Gemini didn't mention, that's important — it means you need to address it in your paper.

---

### Phase 2 — Synthesis (Day 2–3)

After collecting all NotebookLM responses, answer these four questions yourself using the collected material:

**Synthesis Q1:** Does NotebookLM confirm that no paper has done moral probing for age bias? If it finds something, that paper needs immediate manual verification — it could invalidate your novelty claim.

**Synthesis Q2:** What sample size does the methodology literature suggest is sufficient? Warren used 100 images per prompt. Is 20–30 per prompt defensible for a pilot study framing? NotebookLM's answer to Notebook A Q3 will tell you.

**Synthesis Q3:** What VLM prompting strategy do prior papers use for automated annotation? Use this directly to design your GPT-4o-mini schema — don't invent from scratch.

**Synthesis Q4:** What statistical corrections do papers use for multiple prompt comparisons? You're running 20 prompt pairs × 2 dimensions × 3 models — that's a multiple comparisons problem. NotebookLM A Q5 will tell you the standard approach.

---

### Phase 3 — Pilot Experiment (Day 3–5, before full commitment)

This is your actual go/no-go gate. Do this before spending any real money.

**Step 1:** Generate 50 images using FLUX.1-dev on free Colab tier. Use 5 prompt pairs from Warren (pick the ones with largest weight difference: gluttonous/moderate, lazy/diligent, greedy/charitable, immoderate/austere, and one neutral pair like rational/irrational).

**Step 2:** Manually label all 50 images yourself for: weight category (underweight/normal/overweight/obese) and age category (young/middle-aged/elderly). This is your ground truth.

**Step 3:** Run GPT-4o-mini Batch API on same 50 images with your designed VLM prompt. Cost: under ₹100.

**Step 4:** Compute agreement between your labels and GPT-4o-mini's labels. Calculate Cohen's Kappa. If Kappa > 0.7 for both weight and age — green light, proceed to full run. If Kappa is 0.5–0.7 — refine your VLM prompt and re-test. If Kappa < 0.5 — the automated annotation approach has a problem and you need to rethink measurement.

**Step 5:** Also check at this stage — do the 50 FLUX images show any weight or age variation at all? If FLUX generates uniformly normal-weight young adults regardless of prompt, there's no signal to measure and the study is DOA regardless of annotation quality.

---

### Phase 4 — Full Design Decisions (Day 5–6, after pilot passes)

Only proceed here if pilot passes. Use NotebookLM synthesis + pilot results to finalize:

**Decision 1 — Final prompt pairs:** Keep all 20 Warren pairs, or add/replace some with age-salient pairs? Candidates to add: "wise/foolish", "experienced/naïve", "established/ambitious". Decision criteria: do Warren's existing pairs already surface age signal in your pilot? If yes, keep them unchanged. If not, add 3–5 age-salient pairs.

**Decision 2 — Models:** Confirm which 3 models are feasible on Colab Pro A100 within budget. FLUX.1-dev is confirmed. SDXL is confirmed. SD3.5 Large needs ~12GB VRAM — check A100 availability. If SD3.5 is problematic, substitute SD 2.1 or SDXL-Turbo.

**Decision 3 — Image count:** Based on pilot signal strength and sample size guidance from NotebookLM, finalize how many images per prompt per model. Minimum defensible: 50 per prompt. Warren used 100. For pilot study framing, 50 is acceptable if you state it explicitly.

**Decision 4 — Statistical pipeline:** Finalize which tests based on NotebookLM findings. Baseline: Chi-Square + Cramér's V + BH-FDR correction. Add Mann-Whitney U if you're comparing continuous age/weight scores rather than categories.

---

### Phase 5 — Execution (Week 2–6)

Split tasks between you and Ishuvi:

**Pragyan:** Image generation pipeline, VLM annotation Batch API, statistical analysis (you have this from DCDD)

**Ishuvi:** Prompt documentation, manual spot-check validation, results interpretation, related work section

Week 2: Full image generation across all models and prompts Week 3: VLM annotation run + manual spot-check (10% sample) Week 4: Statistical analysis + visualization Week 5: Writing — introduction, methodology, results Week 6: Discussion, related work, abstract, revision

---

### Phase 6 — Go/No-Go for Workshop Submission (End of Week 6)

After ArXiv upload, evaluate: is the cross-dimensional finding (fat + age in same negative prompts) strong enough and statistically clean enough to warrant a workshop submission? Target venues in order of fit: FAccT 2026 workshops, CVPR 2026 fairness/bias workshops, AAAI AIES 2027.

If results are marginal — ArXiv only. That still gives you the internship certificate and a citable preprint for your MS applications.

---
