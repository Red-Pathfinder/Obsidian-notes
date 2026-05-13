**Date:** 2026-05-12

**Paper Target:** EMNLP 2026

**Central Thesis:** The Bias Cascade (Socioeconomic → Agency → Demographic)

---

## 🌊 The Core Theory: The Bias Cascade

> [!ABSTRACT]
> 
> Disability-Conditioned Demographic Drift (DCDD) is not a set of isolated errors. It is a mechanistic chain reaction.

1. **Socioeconomic Anchor:** Disability tokens trigger "clinical/medical" latent clusters.
    
2. **Agency Penalty:** The medical context forces a "patient" schema (passive, assisted).
    
3. **Identity Collapse:** The high "cognitive load" of resolving disability + medical context causes the model to dump intersectional features, reverting to White/Male priors.
    

---

## 🛠️ Tier 1: Inference-Time (No Retraining)

_Quick-fix strategies for current T2I models._

### 1. Semantic Anchoring

- **Logic:** Use weighted clauses to force the model to stay in the "Professional" domain.
    
- **Prompt Structure:** `(Professional Anchor:1.5) + (Identity Stabilizer:1.2) + (Disability Modifier:0.8)`
    
- **Example:** `(software engineer in office:1.5), (Black woman:1.2), (uses a wheelchair:0.8)`
    

### 2. Negative Attribute Grounding

- **Logic:** Actively subtract the clinical attractor basin from the CFG (Classifier-Free Guidance) path.
    
- **Target Tokens:** `hospital, clinic, patient, gown, assisted, passive, hunched.`
    

### 3. Cross-Attention Steering (ITAA)

- **Logic:** A programmatic hook to boost attention weights for identity/professional tokens if the disability token begins to dominate the spatial map.
    

---

## ⚖️ Tier 2: Alignment & Fine-Tuning

_Architectural fixes for model creators._

|**Technique**|**Mechanism**|**Goal**|
|---|---|---|
|**Counterfactual DPO**|Use the 385 pairs as Preference Data (Neutral=Win, Biased=Loss).|Train the model to prefer equity over stereotypes.|
|**Multi-Head Reward**|Separate heads for Agency, Socioeconomics, and Identity.|Penalize specific harms independently.|
|**Identity-Preserving LoRA**|Fine-tune on agentive disability imagery with a consistency loss.|Prevent feature collapse during conditioning.|

---

## 📂 Tier 3: Data Strategy (The Root Cause)

_Fixing the "Dataset Ideology" in LAION/CommonCrawl._

### 1. Semantic Uncoupling

- **Strategy:** Curate a "Contrastive" dataset.
    
- **Goal:** Train the embedding space (CLIP/T5) to recognize that "Wheelchair" and "Office" are just as probable as "Wheelchair" and "Hospital."
    

### 2. Agentive Re-Authoring

- **Strategy:** Use LLMs to rewrite passive alt-text.
    
- **Change:** "Disabled person being helped" → "Researcher using an adaptive device to conduct experiments."
    

---

## ⚠️ Methodological Red Flags

> [!WARNING] The Circular Dependency Problem
> 
> Our VLM auditor (`gpt-5-mini`) was likely trained on the same biased data as FLUX/SD. It may be "blind" to the Agency Penalty.
> 
> **Fix:** Conduct a 10% human-in-the-loop validation using the **Social Model of Disability** rubric.

---

## 🚀 Immediate Next Steps

- [ ] **Mitigation Test:** Run 50 "Anchored Prompts" on SD 3.5.
    
- [ ] **Figure Mining:** Select "Exemplar Pairs" for the "Grid of Shame."
    
- [ ] **Drafting:** Begin the "Bias Cascade" section in the Discussion.