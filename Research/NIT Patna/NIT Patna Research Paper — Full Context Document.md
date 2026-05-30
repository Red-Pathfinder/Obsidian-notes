**Last updated:** May 30, 2026  
**Authors:** Pragyan Prayas Jena, Ishuvi Misra (KIIT University)  
**Supervisor:** Dr. Krishan Kumar Sethi, NIT Patna  
**Goal:** ArXiv preprint + internship certificate | Stretch: Workshop submission

---

## 1. Who We Are & Constraints

|Parameter|Detail|
|---|---|
|Team|2 researchers (Pragyan + Ishuvi)|
|Timeline|June 10 → July 31, 2026 (8 weeks)|
|Budget|Max ₹5,000 total (reserve ₹2,000 for Colab Pro)|
|GPU (until ~June 20)|Google Colab / cloud GPU|
|GPU (after June 20)|MacBook Air M5 24GB — good for inference, NOT training|
|Primary value|Internship certificate for MS applications|
|Stretch goal|Workshop paper submission|
|MS Target|Germany (Freiburg, TUM, Würzburg, FAU Erlangen) + Nordics backup|
|Research focus|Trustworthy AI / Computational Fairness|

**Existing paper context:** Pragyan is simultaneously co-authoring the DCDD paper ("Disability-Conditioned Demographic Drift in Text-to-Image Models") targeting WACV 2026 — already has pipeline experience with FLUX.1 [dev], OpenAI Batch API (GPT-4o-mini), SigLIP/CLIP embeddings, Chi-Square, Cramér's V, Benjamini-Hochberg FDR.

---

## 2. The Anchor Paper — Warren et al. (NAACL 2025)

**Full title:** "Decoding Fatphobia: Examining Anti-Fat and Pro-Thin Bias in AI-Generated Images"  
**Authors:** Jane Warren, Gary Weiss, Fernando Martinez Lopez, Annika Guo, Yijun Zhao  
**Venue:** Findings of NAACL 2025  
**DOI:** 10.18653/v1/2025.findings-naacl.266

### What they did

- Generated **4,000 images** using DALL-E 3
- Used **20 pairs of morally-valenced prompts** (e.g., "gluttonous" vs. "moderate", "lazy" vs. "diligent", "immoral" vs. "moral") — crucially, NO explicit physical descriptors in any prompt
- **4 human raters** labeled each image on a **1–10 weight scale** borrowed from Harris et al. (2008) BMI pictorial reference
- Weight categories mapped to CDC definitions: underweight (1–2), normal (3–5), overweight (6–7), obese (8–10)

### Key findings

- DALL-E 3 **completely excluded fat bodies from all positive-prompt images** — zero overweight/obese people across all morally positive prompts
- Fat bodies appeared almost exclusively in **negative moral prompts** (greedy, lazy, gluttonous, immoderate)
- Largest weight difference: "gluttonous" vs. "moderate" = 3.30 points — 42% of "gluttonous" images were obese
- AI-generated images showed only 3.4% fat bodies vs. 73% in real US population
- Underweight bodies appeared at **15× the real-world rate** in positive prompts

### Why the framework was reviewer-proof

- The **1–10 weight scale** was borrowed from Harris et al. (2008) — a pre-existing, medically validated instrument
- Weight categories anchored to **CDC BMI definitions** — 50 years of medical consensus
- When a reviewer asks "how do you define overweight?" — Warren cites medical literature, not their own design

### Explicitly stated limitations (their own words)

1. Only studied **DALL-E 3** — no open-weight models tested
2. Relied on **manual human annotation** — expensive, not scalable, introduces annotator bias
3. Did not analyze **intersections** of weight bias with gender, race, culture
4. Prompts limited to **moral characteristics** — did not explore employment, medical, or academic contexts
5. Could be extended to **other models** (Stable Diffusion, Midjourney, FLUX)
6. Could be extended to **other bias dimensions** beyond weight

---

## 3. Literature Landscape — What Exists

### 3.1 Foundational T2I Bias Papers (confirmed real)

|Paper|Venue|Models|Bias Dimension|Method|
|---|---|---|---|---|
|Warren et al. (2025)|NAACL 2025|DALL-E 3|Body weight / fatphobia|Manual annotation, moral prompting|
|Bianchi et al. (2023)|FAccT 2023|SD v1.4, v2, DALL-E 2, Midjourney|Race, gender, occupation|FairFace classifier, CLIP|
|Luccioni et al. (2023)|NeurIPS 2023|SD v1.4, v2, DALL-E 2|Gender, ethnicity, profession|CLIP/SigLIP embedding analysis|
|Jha et al. / ViSAGe (2024)|ACL 2024|SD v1.4|Nationality stereotypes|Manual + VLM (CLIP+BART)|
|Cho et al. / DALLEval (2023)|ICCV 2023|DALL-E 2, SD, minDALL-E|Gender, skin tone|PaintSkills dataset|
|Porikli & Porikli (2025)|CVPR 2025 EMACS|SD 1.5, FLUX.1|Gender, race, age, somatotype|16,000 images vs. Google Search|
|Wilson et al. (2025)|AIES 2025|SD v1.5, v2.1, SDXL|Skin tone homogeneity|Perceptual metrics (ΔE)|
|Vandewiele et al. (2025)|arXiv:2510.00045|HunyuanImage, Qwen, FLUX.1-dev, SD 3.5, SDXL|Gender, occupational stereotypes|100 images × 5 professions × 5 qualifiers|
|Vonderhaar et al. (2025)|AIES 2025|FLUX.1|LGBTQ+ representation|OFAT counterfactual prompting|

### 3.2 Disability Representation Papers (confirmed real)

|Paper|Venue|Key Finding|
|---|---|---|
|Tevissen (2024)|CVPR AVA Workshop|Models depict disabled people as elderly, sad, wheelchair-bound|
|Mack et al. (2024)|CHI 2024|Wheelchair used as universal proxy for all disability|
|Tian et al. (2026)|arXiv|SDXL + DALL-E 3; affective framing + sentiment polarity for disability — **closest methodological neighbor to our work**|
|Ertman et al. (2025)|Rehabilitation Psychology|DALL-E 3 medicalizes disability — 64% of cases ignored semantic instructions|

### 3.3 Critical Gap Summary

|What EXISTS in literature|What does NOT exist|
|---|---|
|Fat bias in DALL-E 3 (Warren)|Fat bias in FLUX.1, SDXL, SD3.5|
|Disability bias broadly (Tian, Mack)|Age bias via moral probing|
|Multi-model gender bias (Vandewiele)|Multi-model body/physical condition bias|
|Somatotype as one variable in broad sweep (Porikli)|Somatotype + moral probing as dedicated study|
|Manual annotation for weight (Warren)|VLM-automated annotation for body bias|
|Single-model weight study (Warren)|Cross-model weight bias comparison|

**Confirmed:** No paper has replicated or extended Warren et al. (2025) on any other model. Zero.

---

## 4. Our Research Direction — How We Got Here

### 4.1 What we considered and rejected

**Option: Vitiligo as extension probe**

Initial idea was to use Warren's moral probing framework and extend it to ask: _does the moral-body conflation extend to visible skin conditions like vitiligo?_

**Why we rejected it:**

- Warren's framework worked because the CDC weight scale + Harris et al. (2008) pictorial instrument provided a **pre-existing, medically validated anchor**. A reviewer can't challenge the measurement instrument.
- For vitiligo, no equivalent validated scale exists for _social representation_ (as opposed to clinical severity, which uses VASI/VETF — different purpose entirely)
- More fundamentally: vitiligo doesn't map onto the **cultural-moral script** the way fatness does. Fatness is culturally coded as behavioral (gluttony, laziness) — a _choice_ — which is why moral prompts surface it. Vitiligo has no equivalent moral vocabulary in Western cultural scripts. T2I models would likely _erase_ vitiligo regardless of prompt valence — which is a different finding requiring a different research design.
- A SAM-based vitiligo segmentation paper exists (Torgal et al., TIACOMP 2024) but it's a clinical tool, not a social bias auditing framework — no bridge to our use case.

**Conclusion:** Vitiligo deserves its own paper with its own bespoke design. Not a 8-week extension.

### 4.2 The question that led to the right direction

> "Is there any other category that is similar to fat — that can actually be studied using moral attributes the way Warren studied fatness?"

**The four conditions a characteristic must satisfy:**

1. Must be culturally coded as partly a _choice_ or _behavioral outcome_ — not purely fate/genetics
2. Must have a documented history of **moral language** being applied to it
3. That moral vocabulary must plausibly exist **at scale in T2I training data**
4. The characteristic must be **visually measurable** in generated images

### 4.3 Candidates evaluated

|Category|Cultural-Moral Script|Visual Measurability|Verdict|
|---|---|---|---|
|**Aging / Old age**|Strong — "past it", "burden", "irrelevant", productivity = youth|Solved — face age estimation well-validated|✅ STRONG|
|Poverty markers|Moderate — laziness, bad choices|Weak — no validated classifier|⚠️ Moderate|
|Skin tone|Very strong|Solved|❌ Saturated in literature|
|Addiction markers|Strong|Very weak — T2I inconsistent|❌ Weak|
|Muscularity/fitness|Moderate (reversed direction)|Moderate|❌ Weak research question|
|Mental illness|Strong|Very weak — no visual markers|❌ Problematic|

### 4.4 Why Aging works

Aging satisfies all four conditions:

**The cultural-moral script is rich and ancient:**

- Old age = "past their prime", "burden on society", "incompetent", "irrelevant", "unproductive"
- Youth = vitality, moral energy, productivity, ambition, potential
- This maps directly onto Warren's prompt pairs — "productive/unproductive", "competent/incompetent", "diligent/lazy", "strong-willed/weak-willed" will all plausibly surface age bias

**Measurement is solved:**

- Face age estimation is a mature CV problem
- GPT-4o-mini can reliably estimate perceived age from generated images
- CLIP zero-shot age classification is well-documented
- No new framework needs to be designed — age is a continuous variable like weight

**No prior work:**

- Porikli & Porikli (2025) mention age as one variable in a broad intersectional sweep, but **no paper has used moral probing to surface age bias in T2I models**
- This is a confirmed gap

**Connects to existing literature:**

- Ageism is recognized alongside ableism and fatphobia in critical theory literature
- The same Western capitalist value system that associates thinness with productivity also associates youth with productivity — reviewers will recognize the theoretical coherence

---

## 5. Proposed Paper Design

### Title (working)

_"Beyond the Body: Moral Framing as a Probe for Weight and Age Bias in Text-to-Image Generative Models"_

### Core Contributions

1. **Multi-model replication** of Warren et al.'s moral probing methodology across open-weight models (FLUX.1-dev, SDXL, SD3.5) — first cross-model weight bias study
2. **Methodological upgrade**: Replace manual human annotation with GPT-4o-mini VLM-based automated judgment via Batch API — directly addresses Warren's stated limitation
3. **Novel dimension**: Apply identical methodology to age bias — first moral probing study for ageism in T2I models
4. **Cross-dimensional finding**: Do the same moral prompts surface both weight AND age bias simultaneously? — genuinely novel intersectional question

### Study Structure

**Study 1 — Weight Bias Replication (Multi-Model)**

- Same 20 moral prompt pairs from Warren et al.
- Models: FLUX.1-dev, SDXL, SD3.5 (all open-weight, all on Colab)
- ~400–600 images total (smaller than Warren's 4,000 — pilot study framing)
- Measurement: GPT-4o-mini Batch API with Pydantic schema for perceived weight category
- Statistics: Chi-Square, Cramér's V, BH-FDR (same as DCDD paper — reuse pipeline)

**Study 2 — Age Bias (Novel Dimension)**

- Same 20 moral prompt pairs
- Same 3 models
- Measurement: GPT-4o-mini Batch API — perceived age category (young adult / middle-aged / elderly)
- Statistics: Same pipeline

**Cross-cutting Analysis**

- Are images generated from negative prompts simultaneously heavier AND older?
- Does the model construct a composite "morally bad body" (fat + old) vs. a composite "morally good body" (thin + young)?

### Measurement Framework

**For weight (already validated):**

- Borrow Warren's exact instrument: CDC weight categories (underweight / normal / overweight / obese)
- VLM prompt: _"Looking at this image, estimate the perceived body weight category of the person depicted. Choose one: underweight, normal weight, overweight, obese. Base your judgment on visual appearance only."_

**For age (validated by existing literature):**

- Age categories: young adult (18–35), middle-aged (36–60), elderly (60+)
- These map to standard demographic categories used across the bias literature
- VLM prompt: _"Looking at this image, estimate the perceived age group of the person depicted. Choose one: young adult (18–35), middle-aged (36–60), elderly (60+). Base your judgment on visual appearance only."_

### Compute & Budget Estimate

|Item|Cost|
|---|---|
|Colab Pro (2 months)|₹2,000|
|OpenAI Batch API — GPT-4o-mini (600 images × 2 attributes)|~₹500–800|
|Image generation (FLUX.1-dev on Colab)|Free tier sufficient|
|Buffer|₹1,200–1,500|
|**Total**|**~₹3,500–4,300**|

Within ₹5,000 budget.

---

## 6. Technical Pipeline (Reusing DCDD Infrastructure)

```
1. Prompt construction (20 pairs × 3 models = 60 prompt-model combos)
2. Image generation — FLUX.1-dev / SDXL / SD3.5 via diffusers on Colab
3. Image storage — Google Drive (free)
4. VLM annotation — OpenAI Batch API with GPT-4o-mini
   - Pydantic schema: {weight_category, age_category, confidence}
   - Batch size: all images in one job
5. Statistical analysis — Chi-Square, Cramér's V, BH-FDR
6. Transition matrices (per model, per prompt polarity)
7. Visualization — matplotlib / seaborn
```

**Pragyan already has this pipeline from DCDD.** Adaptation effort is low.

---

## 7. Papers to Load into NotebookLM

### Notebook A — Methodology Papers

- Warren et al. NAACL 2025 _(PDF in hand)_
- Luccioni et al. NeurIPS 2023 (arXiv:2303.11408)
- Jha et al. ACL 2024 (arXiv:2401.06310)
- Vandewiele et al. arXiv:2510.00045
- Porikli & Porikli CVPR 2025 (arXiv:2506.13780)

### Notebook B — Domain / Gap Papers

- Tian et al. 2026 (disability + affective framing — closest methodological neighbor)
- Mack et al. CHI 2024 (disability representation)
- Bianchi et al. FAccT 2023
- Wilson et al. AIES 2025

### NotebookLM Query — Notebook A

_"What methodological gaps exist in how body-related bias is measured in T2I models? Specifically: what are the limitations of manual annotation, and which papers propose automated or VLM-based alternatives? What has been done for multi-model comparisons?"_

### NotebookLM Query — Notebook B

_"Which physical or bodily characteristics have NOT been studied using moral framing as a probe in T2I models? What population groups remain completely absent from T2I bias auditing literature? Is there any work combining age bias with moral probing?"_

---

## 8. Open Questions (To Resolve Before Writing)

1. **Pilot validation:** Does GPT-4o-mini reliably estimate weight AND age categories from FLUX-generated images? Need 50-image manual spot-check before committing to full run.
2. **Prompt pairs:** Do Warren's exact 20 pairs work for age probing? Or do we need to add/modify some pairs that have stronger age-moral associations (e.g., "wise/foolish", "experienced/naive")?
3. **Model selection:** SD3.5 requires more VRAM — confirm Colab Pro A100 availability before committing.
4. **Image count:** 600 total (100 per model × 2 prompts per pair × 3 models × ~1 image per prompt) — is this statistically sufficient for Chi-Square? Warren used 100 per prompt. Need power analysis.
5. **Framing:** ArXiv preprint vs. workshop target — if workshop, which one? (FAccT workshops, CVPR fairness workshops, AAAI AIES are candidates)

---

## 9. What This Paper Is NOT

- Not a replication for its own sake — the methodological upgrade (VLM automation) and age dimension are genuine contributions
- Not a vitiligo paper — that idea was considered and rejected (no validated framework, no moral-cultural script mapping)
- Not an NLP paper — fully CV/multimodal, consistent with Pragyan's MS profile pivot
- Not reliant on expensive proprietary APIs for generation — all open-weight models

---

## 10. Reviewer Risk Assessment

|Potential challenge|Our defense|
|---|---|
|"This is just a replication of Warren"|Multi-model + VLM automation + age dimension = 3 new contributions|
|"Your weight measurement isn't validated"|We use Warren's exact instrument (CDC categories + Harris et al. 2008)|
|"Your age measurement isn't validated"|Standard demographic age buckets used across bias literature; GPT-4o-mini age estimation validated in prior VLM papers|
|"Small sample size"|Explicitly framed as pilot study; statistical tests appropriate for sample size; future work section addresses scale|
|"FLUX wasn't aligned the same way as DALL-E"|This is a feature, not a bug — cross-architecture comparison is the point|
|"Why these specific moral prompts?"|Borrowed directly from Warren et al. — reviewer cannot challenge what they already accepted at NAACL|