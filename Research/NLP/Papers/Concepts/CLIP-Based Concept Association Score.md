($CAS_{CLIP}$)

**Tags:** #AI #MachineLearning #CLIP #Embeddings #BiasDetection #ComputerVision #Counterfactuals

### 1. The Embedding Process

Method 2 utilizes [[CLIP]] (Contrastive Language-Image Pre-training) to directly encode images into a high-dimensional vector space.

- Every image in the **Initial Prompt Set** ($I_P$) and the **Counterfactual Prompt Set** ($I_{Pcf}$) is converted into an embedding.
    
- These embeddings capture the semantic and visual essence of the image in a mathematical format.
    

### 2. Measuring Similarity ([[Cosine Similarity]])

The similarity between the original prompt results and the counterfactual results is measured by calculating the cosine similarity between their respective vectors.

- **Range:** Values range from **0 to 1**.
    
- **1:** Indicates a complete conceptual match (the change in the prompt did not significantly alter the output content).
    
- **0:** Indicates no association (the change in the prompt resulted in completely different visual concepts).
    

### 3. The Formula

The final score is the mean of the cosine similarities across all image pairs between the two sets:

$$CAS_{CLIP} = \text{mean} \left[ \text{cosine}(\text{CLIP}(I_i), \text{CLIP}(I_{cf})) \right]$$

$$\forall I_i, I_{cf} \in I_P, I_{Pcf}$$

---

### Comparison: VQA vs. CLIP Embedding

> [!INFO] **Post-hoc [[Explainability]]**
> 
> Unlike Method 1 ([[VQA]]), which provides a list of specific word frequencies (e.g., "apron" vs. "suit"), Method 2 is limited in explainability. It can quantify **that** a difference exists, but it cannot explain **what** specific objects or attributes changed to cause that difference.

|**Feature**|**[[VQA]]-based CAS**|**[[CLIP]]-based CAS**|
|---|---|---|
|**Data Source**|Natural Language Descriptions|High-dimensional Vectors|
|**Explainability**|High (provides entity lists)|Low (mathematical distance only)|
|**Processing**|Slow (requires LLM generation)|Fast (direct matrix calculation)|
|**Precision**|Semantic/Explicit|Visual/Implicit|

---

### See Also

- [[Counterfactuals]]
    
- [[Mean Absolute Deviation]]
    
- [[T2IAT]]