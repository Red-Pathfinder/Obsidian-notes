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

Ans - **Documented Limitations of Manual Human Annotation**

Evaluating body-related bias and social identity in generated images relies heavily on human judgment, but the sources identify several critical limitations to manual annotation:

- **Subjectivity and Categorical Ambiguity:** Identifying physical traits relies intrinsically on subjective human perception, and defining boundaries between body types is difficult. For instance, when attempting to measure weight bias (fatphobia), researchers note that "fatness" is a highly porous category with permeable boundaries, making it difficult for annotators to draw objective lines between weight classifications like "overweight" or "obese". Similarly, determining whether a stereotype is strictly "visual" versus "non-visual" often invites annotator subjectivity.
- **Inability to Determine Identity from Appearance:** A fundamental limitation is that complex, multidimensional social identities cannot be accurately deduced solely from visual markers. For example, even human annotators cannot reliably estimate a person's gender across a broad spectrum based strictly on appearance. Applying the same logic to race, researchers note that race is a socially constructed concept, meaning that inferring racial identity or ethnicity from visual appearance alone is fundamentally flawed and likely to yield inaccurate results. Because of these limitations, researchers using manual annotation are often forced to reduce identities into binary or overly simplistic categorizations, which can perpetuate the very algorithmic harms they are trying to measure.
- **Resource Intensity:** On a practical level, manually annotating text-to-image (T2I) outputs at a scale large enough to identify statistically significant biases is highly resource-intensive and time-consuming.

**Automated Alternatives and Their Validation**

To bypass the bottlenecks and label-assignment issues of manual annotation, three papers propose automated measurement techniques and validate them using diverse methods:

**1. Cho et al. (DALL-EVAL)**

- **Proposed Alternative:** To measure gender and visual attributes, the authors utilize **BLIP-2**, an automated Visual Question Answering (VQA) model, asking it targeted questions like _"the person looks like a male or a female?"_. To measure skin tone without assigning racial categories, they propose a pipeline using **FAN** to detect facial landmarks and **TRUST** to estimate scene illumination and facial albedo. They then calculate the Individual Typology Angle (ITA) from the albedo and map it to the 10-point Monk Skin Tone (MST) scale.
- **Validation Steps:** The authors rigorously validated these automated models against expert human annotators. For gender and attributes, BLIP-2's automated answers achieved **99.2% and 91.71% accuracy**, respectively, when compared to human expert judgments. For skin tone, the researchers first trained two expert annotators on the Monk Skin Tone Examples dataset to establish a highly accurate human baseline. They then compared different automated segmentation techniques against this human baseline, proving that their light-aware (albedo + ITA) method was the most accurate automated alignment with human perception.

**2. Luccioni et al. (Stable Bias)**

- **Proposed Alternative:** To avoid a "poorly-specified" human label assignment problem, the authors use a **cluster-based visual feature analysis** alongside text-feature extraction. First, they generate textual representations of generated images using a captioning model (ViT GPT-2) and VQA (BLIP) to automatically search for gender-marked keywords. Second, they use BLIP VQA to extract dense image embeddings and **cluster them into 24 distinct regions** using a Ward linkage criterion. This allows them to mathematically quantify the distribution of generated images across different visual identity regions without explicitly labeling the specific gender or ethnicity of any individual image.
- **Validation Steps:** The authors validated the reliability of their clustering by visually inspecting the generated images assigned to specific clusters to ensure the visual representations were "coherent with the region summaries". They also developed interactive neighborhood-lookup tools and an "Average Face Comparison Tool" (which aligns facial features using the Facer package) to qualitatively verify that the automated clusters properly grouped structural similarities and visual traits.

**3. Jha et al. (ViSAGe)**

- **Proposed Alternative:** To detect geographic and cultural stereotypes at scale, the authors automatically generated image captions using **CLIP embeddings combined with a BART model**. They then performed automated string matching against a known database of visual stereotypes to see if stereotypical attributes (like "sombrero" or "poor") appeared in the top 50 generated captions for an image. They used a modified tf-idf metric to generate a salience score quantifying how uniquely specific attributes were associated with different identities.
- **Validation Steps:** The researchers validated their automated text-based pipeline by comparing its outputs against large-scale manual human annotations. They found that the automated approach successfully uncovered objective visual stereotypes that aligned with human perception, noting that the automated system's most salient attributes had a **high likelihood (44.69%)** of also being marked as present by human annotators.

**Q2 (VLM annotation):**

> "Which papers in this notebook use Vision-Language Models (like GPT-4V, LLaVA, or GPT-4o) to annotate or classify generated images? What prompting strategies did they use, and what were the known failure modes or hallucination risks they identified?"

Ans - None of the papers in the provided sources use advanced Vision-Language Models (VLMs) like GPT-4V, LLaVA, or GPT-4o for annotating or classifying generated images. In fact, some papers intentionally avoid automated annotation altogether; for example, both Vandewiele et al. and Warren et al. rely strictly on manual human evaluation to classify gender and weight, respectively, to ensure accurate identification of visual traits without relying on opaque tools.

However, several papers do use older VLMs (such as BLIP, BLIP-2, and CLIP) for automated annotation. Here are the prompting strategies they utilized and the failure modes they identified:

**1. Cho et al. (DALL-EVAL) - Using BLIP-2**

- **Prompting Strategy:** To detect gender, the authors provided BLIP-2 with generated images and asked the visual question, _"the person looks like a male or a female?"_. To detect specific attributes (like clothing), they used the prompt, _"Is the person wearing A?"_ (e.g., "a suit" or "jeans") and checked if the model responded with "yes".
- **Failure Modes & Model Comparison:** The authors explicitly tested CLIP (ViT/B-32) for these same tasks and found it to be highly failure-prone. For instance, on a benchmark gender dataset, CLIP achieved only 66% accuracy compared to BLIP-2's 82%, and CLIP also exhibited a much higher baseline gender bias. When detecting attributes, CLIP performed significantly worse against expert human annotation compared to BLIP-2.

**2. Luccioni et al. (Stable Bias) - Using BLIP VQA and ViT GPT-2**

- **Prompting Strategy:** The authors used a Visual Question Answering model (BLIP VQA) to extract short text representations of generated figures by asking, _"What word best describes this person’s appearance?"_. They also used an image captioning model (ViT GPT-2) to generate multi-word, open-ended captions for the images without constraining the models to pre-defined labels.
- **Failure Modes Identified:** The authors stress a major limitation: the VQA and image captioning models inherently possess their own confounding factors and social biases inherited from their training data. Because the models themselves are biased (such as associating women with shopping), their text outputs cannot be interpreted as an objective "ground truth" of what is in the image.

**3. Jha et al. (ViSAGe) - Using CLIP + BART**

- **Prompting Strategy:** The authors automatically generated captions for generated images using CLIP embeddings combined with a BART model, producing the top 50 descriptive captions for each image. They then searched these captions for known visual stereotypes.
- **Hallucination Risks Identified:** A significant failure mode identified in this automated text-generation approach was the hallucination of cultural stereotypes. The authors noted that the captioning model sometimes identified stereotypical attributes—such as a "cow" or an "elephant" in images generated for "Indian" identities—even when those objects were not actually depicted in the generated images. They concluded that this hallucination is likely due to pre-existing errors and biases embedded within the captioning model itself.

**Q3 (Multi-model comparison):**

> "What methodological choices did papers make when comparing bias across multiple T2I models — specifically around sample size, prompt standardization, and statistical tests? What sample sizes were considered sufficient for Chi-Square or similar tests?"

Ans - When comparing bias across multiple Text-to-Image (T2I) models, researchers made specific methodological choices to ensure that their comparisons were reliable, objective, and accurately reflected the models' intrinsic behaviors.

**Prompt Standardization** To ensure that variations in the generated images were caused by the models themselves rather than inconsistencies in the text inputs, researchers relied on highly structured, unified prompt grammars:

- **Controlling Scene and Style:** Vandewiele et al. intentionally avoided simple role-only prompts (like "a surgeon"), which frequently cause models to generate ambiguous group scenes. Instead, they utilized a strict grammar template: `<image qualifier>, a <portrait qualifier> portrait of a <hospital role>`. They also forced all models to adopt the same photorealistic style by prepending a standardized image qualifier ("high quality, detailed and ultra realistic photography, 4K, HDR").
- **Aligning Contexts:** Luccioni et al. used a standardized prefix ("Photo portrait of a [X] [Y]") for all professions. When testing specific identity markers (gender and ethnicity), they explicitly added the suffix "at work" to the prompt so that the resulting backgrounds visually aligned with the workplace settings generated for the profession prompts.
- **Interchangeable Templates:** Cho et al. evaluated bias across models by generating combinations using the strict template `"[Gender] who works as a/an [Profession]"`.

**Sample Size** Across the studies, generating **100 images per specific prompt configuration** emerged as a standard methodological choice for establishing sufficient analytical volume:

- Vandewiele et al. generated 100 images for each combination of role, qualifier, and model, resulting in a robust dataset of 15,000 images.
- Warren et al. generated 100 images for each of their 40 moral characteristic prompts, producing 4,000 total images.
- Bianchi et al. similarly generated 100 images per descriptor or occupation when testing Stable Diffusion.
- For methodologies that relied on a massive variety of prompt combinations rather than deep variations of a single prompt, smaller per-prompt samples were used. For example, Jha et al. generated 15 images per identity group, and Cho et al. generated 9 images per prompt across 252 diagnostic combinations.

**Statistical Tests and Chi-Square Sufficiency** The provided sources **do not contain any mentions of Chi-Square tests**, nor do they document what sample sizes would be considered sufficient for them. However, the sources do outline the sample sizes used for other specific statistical tests to compare bias:

- **Single-Tailed T-Tests:** Warren et al. used a single-tailed t-test to calculate the statistical significance (p-values) of weight differences between images generated from paired positive and negative prompts. They considered their sample size of **100+ images per prompt pair** sufficient to establish a 95% confidence interval (p < 0.05), allowing them to conclude that 16 out of 20 observed weight differences were statistically significant.
- **Bootstrap Estimators:** Luccioni et al. provided 95% confidence intervals using a bootstrap estimator to assess the statistical reliability of their cluster assignments when comparing the gender and ethnicity distributions of the models' outputs against real-world U.S. Bureau of Labor Statistics data.

**Q4 (Moral probing specifically):**

> "Which papers use morally-valenced or sentiment-polarized prompts to probe T2I models for bias, rather than explicit demographic descriptors? What theoretical justification do they give for this indirect probing approach?"

Ans - **Warren et al.** and **Bianchi et al.** both utilize prompts based on traits, sentiments, or moral valence rather than explicit demographic labels to uncover deeply ingrained biases in T2I models.

**Warren et al.** specifically use **morally-valenced prompt pairs** (such as lazy/diligent, pure/impure, and gluttonous/moderate) to investigate weight bias, generating images based strictly on these positive and negative character traits rather than specifying body size. They theoretically justify this indirect probing by arguing that **Western society inherently projects morality onto body weight**. Grounded in sociology and critical fat studies, they explain that Western culture falsely equates thinness with purity, success, and self-discipline, while denigrating fatness as immoral, lazy, or deviant. Because this moralization is used to rationalize the systemic oppression of fat people, the authors argue that it is critical to probe models using morally valenced language to reveal whether AI systems are silently reproducing these harmful, culturally held associations.

**Bianchi et al.** similarly use socially-loaded and sentiment-polarized descriptors (such as "attractive," "poor," "thug," or "terrorist") to test whether models generate harmful stereotypes **without the user ever mentioning race, gender, ethnicity, or nationality**. They justify this approach to explicitly dismantle the ideology of "colorblindness" — the false belief that simply avoiding demographic language in prompts will prevent models from generating biased outputs. By using indirect descriptors, they demonstrate that T2I models inherently entangle seemingly neutral traits with historically marginalized demographic groups, such as incorrectly associating "thug" or "poor person" with Black features, "terrorist" with Middle-Eastern men, and "attractive" strictly with a "White ideal".

**Q5 (Statistical methods):**

> "What statistical tests are used across these papers to measure bias in generated image distributions — Chi-Square, Cramér's V, t-tests, effect sizes? What thresholds or corrections (like Benjamini-Hochberg FDR) are applied for multiple comparisons?"

Ans - 

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
