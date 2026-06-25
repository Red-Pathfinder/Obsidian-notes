# Daily Research Log

## Goal

1. Read the **Abstract**, **Introduction**, **Methodology**, and **Results** of [[Warren et al. 2025]].
2. Find the paper's **GitHub repository** and **dataset**.
3. Generate research questions.

---

## Completed

- Read all planned sections.
- Located the available public resources.
- Generated research questions.

---

## Knowledge Gained

### Facts

1. **Books can be appropriate citations** for conceptual or theoretical discussions.
   - Example:
     - What is [[Fatphobia]]?
     - Why is [[Thinness]] associated with virtue?

2. Warren et al. generated **100 images per prompt**.

3. Using [[Vision-Language Models]] as annotators introduces several risks.
   - Bias inherited from training data.
   - Image misclassification.
   - Difficult to manually verify annotation errors.

---

### Observations

1. Some image-generation requests were initially refused by safety filters.
2. Re-running the exact same request sometimes succeeded.

---

### Inferences

1. **Variance Reduction**
   - The choice of **100 images per prompt** was likely intended to reduce sampling variance and produce more stable measurements.

---

## Open Questions

1. Why do identical prompts sometimes receive different safety decisions?

   **Hypotheses**
   - Safety filters are probabilistic.
   - Backend routing differs between requests.
   - The refusal system is separate from the image-generation model.

2. Can fewer than **100 generated images** still reveal the same statistical signal?

3. Can the paper be reproduced **without generating new images**?

---

## Next Actions

- Find every publicly available resource related to [[Warren et al. 2025]].
- Determine whether the full pipeline can be reproduced using existing resources.

---

## Permanent Notes to Create

- [[Books vs Research Papers]]
- [[Variance Reduction]]
- [[Vision-Language Models as Annotators]]
- [[AI Safety Filters]]
- [[Research Reproducibility]]
- [[Sampling Size in Generative AI Evaluation]]

---

## Suggested Backlinks

[[Warren et al. 2025]]

- [[Fatphobia]]
- [[Thinness]]
- [[Variance Reduction]]
- [[Vision-Language Models]]
- [[Research Reproducibility]]
- [[Bias in AI]]
- [[Image Generation]]
- [[Research Questions]]

---

## Research Insight

A recurring theme is emerging across my reading:

> I am consistently more interested in **methodology** than in reported results.

Recurring interests include:
- experimental design
- reproducibility
- variance reduction
- annotation reliability
- sources of bias

These should become permanent methodology notes rather than remaining inside individual paper summaries.