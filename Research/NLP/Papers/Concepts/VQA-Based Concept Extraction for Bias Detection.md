**Tags:** #AI #MachineLearning #BiasDetection #ComputerVision #VQA #NLP
### 1. The Interview ([[VQA]] Extraction)

For every image the model generates, you ask a set of standardized questions based on the [[Axis of Bias]] you're testing.

- **Targeted Questions:** If testing gender: _"What is the gender of the person?"_
    
- **Template Questions:** For specific biases (like socioeconomic status): _"What is the {wealth level} in the image?"_
    
- **Methodology:** By asking the **same** questions for both the original prompt ($P$) and the [[Counterfactuals|Counterfactual]] version ($P_{cf}$), you ensure the comparison is controlled and fair.
    

### 2. Building the "Concept Set" ($C$)

The raw text answers from the vision-language model (like [[MiniGPT-v2]]) are cleaned and tokenized.

- **Entities ($c$):** Individual descriptors found in answers (e.g., "Stethoscope," "Kitchen").
    
- **Frequencies ($w$):** The total count of that entity across all images for that specific prompt.
    
- **Output:** You generate two frequency distributions: $C_{init}$ (Initial) and $C_{cf}$ (Counterfactual).
    

### 3. The "Histogram" Logic

To prevent fragmented data, a **Concept-Level Matching Algorithm** merges synonyms (e.g., "Doctor" and "Physician" become one node). This results in two simplified histograms of word frequencies.

### 4. Calculating the [[CAS]] (Intersection over Union)

This is the mathematical core used to quantify the similarity between the two concept sets.

- **Intersection ($W \cap$):** The minimum overlap. If "Professional" appears 10 times in $P$ but only 2 times in $P_{cf}$, the intersection is **2**.
    
- **Union ($W \cup$):** The total spread. In the same example, the union is **10**.
    
- **The Formula:**
    
    $$CAS = \frac{\sum W \cap}{\sum W \cup}$$
    

---

### Why This Matters

- **[[Interpretability]]:** Unlike "black box" embeddings, this tells you exactly _which_ words drive the bias (e.g., identifying that "Nurse" is associated with "Female" but never "Male").
    
- **Precision:** It captures semantic content (objects, clothing, settings) rather than just raw pixel differences.