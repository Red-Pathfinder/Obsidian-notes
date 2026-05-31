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

Ans - Across the provided papers, formal statistical hypothesis testing is surprisingly rare. Most papers rely on descriptive statistics, custom mathematical ratios, or spatial distance metrics to quantify bias rather than traditional statistical tests.

Here is a breakdown of the specific tests, metrics, and thresholds used in the sources:

**T-Tests and P-Value Thresholds**

- **Warren et al.** is the only paper that explicitly employs t-tests. They use a **single-tailed t-test** to determine if the average weight of figures generated from negative prompts is significantly higher than those from positive prompts.
- They apply a standard **p-value threshold of 0.05** (a 95% confidence interval) to determine statistical significance, ultimately finding that 16 out of their 20 prompt pairs exhibited statistically significant weight differences.

**Confidence Intervals via Bootstrapping**

- **Luccioni et al.** avoid traditional hypothesis tests but utilize a **bootstrap estimator** to generate 95% confidence intervals. They use this to reliably compare the gender and ethnicity distributions of their generated images (grouped into quintiles) against real-world baseline data from the U.S. Bureau of Labor Statistics.

**Lack of Chi-Square, Cramér's V, and Multiple Comparison Corrections**

- **Chi-Square & Cramér's V:** None of the papers document using Chi-Square tests for categorical distributions or Cramér's V to measure the association between prompts and generated identities.
- **Corrections for Multiple Comparisons:** Even though researchers often tested multiple categories or prompt pairs simultaneously (e.g., Warren et al. testing 20 different prompt pairs), **none of the papers apply or mention multiple comparison corrections** such as the Benjamini-Hochberg False Discovery Rate (FDR) or Bonferroni corrections.

**Alternative Measurements for "Effect Size"** Instead of standardized statistical effect sizes (like Cohen's _d_), several papers propose custom metrics to quantify the magnitude and severity of the observed biases:

- **Mean Absolute Deviation (MAD):** Cho et al. calculate MAD to mathematically measure the distance between a model's generated demographic distribution and an unbiased, uniform distribution. A MAD of 0 indicates an unbiased distribution, while higher numbers indicate a strong skew toward a single demographic.
- **Stereotypical Tendency Ratio ($\theta$):** Jha et al. quantify bias magnitude by calculating a ratio ($\theta$) that divides the likelihood of a model generating a known stereotype by the likelihood of it generating a random, non-stereotypical attribute.
- **Percentage Point Swings (Max - Min):** Vandewiele et al. quantify the sensitivity of models to different prompt framing by calculating the absolute percentage point difference (Max-Min) in male/female representation when the same profession is preceded by different adjectives.

---

### Notebook B — Gap and Domain Questions

**Q1 (Age bias gap):**

> "Is there any paper in this notebook that specifically studies age bias or ageism in text-to-image models using moral or sentiment-based prompting? If not, what do the papers collectively suggest about age as an understudied dimension?"

Ans  - Based on the provided sources, **there is no paper in this notebook that specifically and exclusively focuses on age bias or ageism using moral or sentiment-based prompting.**

The paper that uses explicit moral prompting (e.g., pairing traits like "sinful/virtuous" or "pure/impure") is **Warren et al. (2025)**, but it applies this methodology entirely to study weight bias and fatphobia, not age.

The closest study to your query is **Porikli (2025)**, which investigates T2I stereotypes across _multiple_ demographic dimensions—including age (categorized as young, adult, and senior)—by using prompts with positive and negative attributes, emotions, and ideologies. While not exclusively focused on ageism, Porikli found clear sentiment-based age biases: models like Stable Diffusion 1.5 generated significantly more "senior" faces for negative attributes (23%) than for positive ones (13%). Seniors were also disproportionately generated for low-income occupations compared to high-income ones.

### What the Papers Collectively Suggest About Age as an Understudied Dimension

While age is frequently acknowledged as a major axis of algorithmic bias alongside race and gender, the sources collectively reveal that **age is often treated as a secondary variable, an intersecting stereotype, or an overlooked demographic** rather than the primary focus of investigation.

The papers suggest the following about how age is situated in T2I bias research:

- **Age is weaponized as an intersecting stereotype:** When T2I models depict other marginalized groups, they frequently rely on age as a lazy visual shortcut. Both Mack et al. and Tian et al. observe that generative models consistently and disproportionately depict people with disabilities (such as blind individuals) as older adults or elderly, which incorrectly implies that certain conditions do not exist across all age groups.
- **"Old age" is computationally treated as a stigma:** Wilson et al. explicitly classifies "old age" as a stigmatized physical trait in their taxonomy of identities. Their study groups old age alongside other stigmas to show how SD XL "flattens" the visual representation of marginalized people, rendering their skin tones artificially darker and more homogenized than non-stigmatized subjects.
- **Older adults are missing from qualitative evaluations:** Even when researchers actively design studies to center marginalized communities, older age groups can be overlooked. Mack et al., who conducted a deep, community-centered qualitative analysis on disability representations, explicitly noted that their participant pool "lacked representation of older adults," acknowledging this as a limitation in understanding the full spectrum of representational harm.

In summary, the literature recognizes that T2I models harbor ageist tendencies—often linking older faces to negative attributes, low status, or stigmatized physical conditions—but ageism itself remains a dimension that is usually captured only as a byproduct of studying other biases.

**Q2 (Weight bias gap):**

> "Beyond Warren et al., do any papers in this notebook study body weight or body size bias in T2I models specifically? What do they collectively say about the state of body diversity representation in generative AI?"

Ans - Yes, **Porikli (2025)** explicitly investigates body size bias in T2I models, referring to it as **"somatotype bias"**. To measure this, Porikli categorized the bodies generated by models like Stable Diffusion 1.5 and Flux-1 as underweight, average, or overweight.

Porikli's findings closely mirror the fatphobia identified by Warren et al. Specifically, Porikli found that **T2I models disproportionately associate overweight bodies with negative concepts**. For example:

- Overweight individuals appeared in 29% of images for negative attributes (e.g., ignorant, poor), compared to only 7% for positive attributes.
- Negative actions (e.g., fighting) generated overweight subjects 22% of the time, whereas positive actions (e.g., studying) generated them only 1% of the time.
- Stigmatized or extreme ideologies, such as "terrorist" or "communist," generated significantly higher percentages of overweight bodies (up to 50%) compared to neutral ideologies like "democrat" (0%).

### The Collective State of Body Diversity in Generative AI

Collectively, the literature demonstrates that **generative AI actively resists portraying body diversity, defaulting instead to a narrow, fatphobic visual hierarchy.** The studies point to three major conclusions about how T2I models handle body weight:

**1. The Total Erasure of Fat Bodies in Positive Contexts** Models systematically erase fat bodies when visualizing goodness, success, or purity. Warren et al. found a complete 0% representation of overweight or obese bodies in images generated for positive moral traits like "diligent," "charitable," and "healthy". Even more alarming, models frequently generate clinically underweight bodies to represent these positive traits (e.g., 62% of images for "pure" and 57% for "charitable" depicted underweight subjects). Porikli similarly confirmed that positive actions and attributes predominantly yield "average" or underweight bodies.

**2. The Weaponization of Fatness as a Visual Shorthand for "Badness"** When generative AI does depict larger bodies, it overwhelmingly does so to signify immorality, failure, or deviance. Warren et al. demonstrate that T2I models rely on stereotypical, caricatured fatness to illustrate negative prompts like "gluttonous," "lazy," "greedy," and "immoderate". This directly aligns with Porikli's finding that negative actions and stigmatized ideologies are where overweight bodies are most permitted to exist. Both papers conclude that AI models have encoded historical Western biases that conflate thinness with virtue and fatness with moral depravity.

**3. Drastic Distortion of Real-World Demographics** The generated outputs present a stark demographic distortion of physical reality. While roughly 73% of adults in the United States are classified as overweight or obese, they make up only 3.4% of the bodies generated by DALL-E 3. Conversely, underweight bodies—which comprise about 1.6% of the actual US population—make up over 24% of the AI-generated subjects.

Ultimately, the papers warn that because visual imagery is consumed less critically than text, **T2I models act as a mass-dissemination tool for weight stigma**. By artificially homogenizing the human form and linking higher body weights almost exclusively to negative traits, these models risk deepening real-world discrimination in medical, professional, and social spheres.

**Q3 (Moral conflation):**

> "Do any papers discuss the theoretical mechanism by which T2I models associate non-normative physical characteristics with negative moral or social attributes? What frameworks — semiotic, co-occurrence-based, or otherwise — do they use to explain this?"

Ans -Yes, the papers extensively discuss the theoretical mechanisms driving these biased associations, employing a combination of **technical (co-occurrence-based)** explanations and **sociocultural, psychological, and semiotic frameworks** to explain why T2I models map non-normative bodies to negative traits.

### Technical Mechanisms: Co-occurrence and Bias Amplification

From a technical standpoint, the models derive these associations directly from the statistical co-occurrence of words and images in their training data.

- **Visual-Semantic Alignment:** T2I models rely heavily on encoders like CLIP, which learn joint text-image embeddings from billions of internet-scraped image-caption pairs. This zero-shot learning process inherently captures and magnifies the semantic associations of natural language, bridging physical features with loaded or stigmatized textual descriptions.
- **Distribution Tails and Model Collapse:** The papers note that non-normative identities often represent the "tail of the distribution" (i.e., minority data points) in training datasets. Because newer models progressively lose information about these rare samples, they suffer from bias amplification—or potentially "model collapse"—forcing the model to fall back on the most visually compressed and stereotypical representations of marginalized groups.

### Sociocultural and Psychological Frameworks

To explain _why_ the training data contains these associations to begin with, the authors lean on various established frameworks from the humanities and social sciences:

**1. The Stereotype Content Model (Psychology)** Tian et al. use the **Stereotype Content Model**, a psychological framework evaluating how different social groups are perceived along two axes: warmth and competence. They use this to explain why models might assign different affective framings to different disabilities; for example, people with mobility impairments are traditionally stereotyped as "warm but incompetent" (associated with pity and protection), whereas individuals with psychiatric conditions are often stereotyped as hostile and incompetent.

**2. Western Moralization and Cultural Scripts (Critical Fat Studies)** Warren et al. utilize frameworks from critical fat studies and sociology to explain how weight bias is inherently tied to moral judgment in the "Western imaginary". They trace this mechanism to the permeation of **Protestant Christian values and the "Seven Deadly Sins"** (e.g., sloth, gluttony, greed), which culturally map moral depravity onto fat bodies and moral purity onto thin bodies. Generative models learn these highly moralized sociocultural scripts—such as associating thinness with the capitalist values of intelligence, diligence, and success—and reify them in visual outputs.

**3. Hypodescent (Sociology)** Wilson et al. rely on the sociological concept of **hypodescent** (historically known as the "one-drop rule") to explain how models visually resolve intersecting or ambiguous identities. They provide empirical evidence that when models depict subjects with multiracial identities, they visually compress the representation by assigning the subject to the more stigmatized or "visually subordinate" group—in this case, uniformly generating dark skin tones despite real-world demographic diversity.

**4. Technoableism (Disability Studies)** Tian et al. draw upon the concept of **technoableism**, a theoretical framework coined by Ashley Shew. This framework posits that technological imaginaries inherently treat disabled bodies as "problems" requiring correction or normalization, reinforcing a bias toward non-disabled ways of life. In the context of AI, models synthesize this technoableist assumption by framing the lived experiences of disabled individuals through reductive or disempowering atmospheres.

**5. Rhetorics of Disabled Representation (Visual Culture)** Mack et al. utilize disability studies scholar Rosemarie Garland-Thomson's **rhetorics of disabled representation**—specifically categorizing depictions as "the wondrous," "the sentimental," "the exotic," or "the realistic". They find that T2I models frequently generate images that fall into the "sentimental" category, relying on semiotic shortcuts that view disabled people as incapable or pitiful (e.g., showing them isolated, sad, or hyper-medicalized) rather than providing the "realistic" portrayals of everyday life desired by the community.

**Q4 (Methodological gaps):**

> "Based on all papers in this notebook, what are the three most significant methodological gaps in how T2I bias is currently studied — specifically regarding physical body characteristics beyond race and gender?"

Ans - The three most significant methodological gaps in how text-to-image (T2I) bias is studied regarding physical body characteristics—such as disability, body size, and age—are the reliance on subjective classification systems, the systematic exclusion of "invisible" traits, and the failure to evaluate intersectionality.

**1. Subjective Classification and Reliance on Flawed Taxonomies** While researchers have developed objective, continuous computational metrics for some characteristics—such as the CIELAB color space scale used by Wilson et al. to mathematically measure human perception of skin tones—studying traits like body size and age relies heavily on subjective, discrete human labeling.

- In their study of somatotype and age bias, Porikli acknowledges that forcing human raters to group generated bodies into broad, reductive buckets (e.g., "young/adult/senior" or "underweight/average/overweight") is an inherently subjective methodology limited by cultural differences and personal interpretations.
- Warren et al. relied on raters mapping AI-generated bodies to a 1-10 numerical scale corresponding to clinical Body Mass Index (BMI) categories. The authors explicitly cite this methodology as a limitation, acknowledging that BMI is a highly biased, pathologizing medical metric originally created using data exclusively from Caucasian males, making it a flawed baseline for evaluating the physical diversity of generated bodies.

**2. The Exclusion of "Invisible" Physical Characteristics** Current automated methodologies require highly visible, stereotypical markers to mathematically evaluate bias, which means non-obvious physical conditions are frequently excluded from research entirely.

- Tian et al. intentionally limited their automated CLIP-similarity analysis to physical/sensory disabilities with clear visual cues (e.g., wheelchair users or people with white canes), acknowledging that disabilities without obvious physical markers were entirely left out of the scope of their study.
- Mack et al. notes a core methodological tension in evaluating T2I outputs for traits with "non-imageable features," such as chronic fatigue or autism. Evaluating these representations requires niche community knowledge (such as recognizing a stool in a kitchen as a sign of chronic illness) rather than standard object detection, complicating static visual analysis.
- Wilson et al. similarly points out that many stigmatized identities relate to lived experiences rather than identifiable physical traits, making it exceedingly difficult to identify or evaluate these subjects in visual outputs.

**3. The Lack of Intersectional Evaluation Frameworks** The literature overwhelmingly measures bias on a single axis, failing to capture how T2I models compound biases across multiple physical and social dimensions. Wilson et al. argues that biases exist as complex cognitive interactions across salient features, meaning that isolated, single-category evaluations miss how T2I models visually compress identities.

- Warren et al. explicitly cites their failure to analyze the intersections of weight bias alongside gender, race, or culture as a major limitation, noting that fatphobia structurally compounds the effects of systemic oppression for bodies with intersectional identities.
- Tian et al. similarly points out that their methodology failed to examine how disability intersects with other social categories, restricting a nuanced understanding of how generative models reinforce stereotypes across multiple identity dimensions.
- Mack et al. notes that their prompt engineering did not provide adequate coverage of crucial intersectional contexts, such as evaluating the visual representation of people with multiple overlapping disabilities.

_(Note: Additionally, researchers highlight a gap in the automated evaluation of physical functionality. For instance, Tian et al. suggests that future methodologies need to incorporate advanced computer vision methods—like object detection and pose estimation—to verify if assistive technologies, such as wheelchairs and hearing aids, are actually interacting correctly with the generated physical bodies, rather than just appearing in the image.)_

**Q5 (Your novelty check):**

> "Has any paper in this notebook studied the intersection of body weight bias AND age bias in the same T2I audit study? Has any paper applied moral probing to age as a variable? What would be needed to make such a study credible?"

Ans - **No paper in the notebook evaluates the explicit intersection of body weight and age bias, nor does any paper apply explicit "moral probing" specifically to age.**

While the literature addresses these variables, they are treated in isolation or tested with different frameworks:

- **Porikli (2025)** audits both age (young, adult, senior) and somatotype (underweight, average, overweight) in the same study using the exact same prompts, but evaluates their demographic distributions independently rather than measuring how they intersect.
- **Wilson et al. (2025)** includes both "old age" and "fat/overweight/obese" in their taxonomy of 93 stigmatized identities, but studies their association with darker skin tones rather than their intersection with one another.
- **Warren et al. (2025)** relies on explicit moral probing (e.g., pairing traits like "sinful/virtuous"), but applies this methodology entirely to body weight, explicitly noting that they did not analyze intersections with other demographics.

However, **Porikli (2025)** does apply a closely related sentiment-based probing to age. By evaluating how models respond to "positive and negative attributes" (e.g., smart/attractive vs. ignorant/poor), Porikli found that models exhibit an ageist bias: negative attributes generated "senior" faces 23% of the time, compared to only 13% for positive attributes.

### Methodological Requirements for a Credible Intersectional Study

Based on the methodological gaps identified by the authors across these sources, designing a credible study that successfully intersects body weight, age, and moral probing would require addressing the following challenges:

**1. Replacing Subjective, Pathologizing Classifications** Currently, researchers rely on subjective human raters to classify generated bodies into discrete age or weight buckets based on visual cues. Warren et al. notes that using the Body Mass Index (BMI) scale as a baseline for visual evaluation is inherently flawed, as it relies on a biased, pathologizing metric originally constructed using Caucasian male bodies. A credible study would need to develop a classification framework that acknowledges the fluidity of weight and age without relying on rigid Western medical categories.

**2. Evaluating for Visual Compression and Hypodescent** Because T2I models struggle with complex identities, they often visually compress them. Wilson et al. demonstrates that T2I outputs frequently exhibit "hypodescent," where models resolve intersecting or ambiguous identities by defaulting to the visual markers of the most stigmatized or subordinate group. A credible study would need to evaluate whether prompting for an older, fat person causes the model to compound the stigmas (e.g., generating exaggerated caricatures of decline) or if it simply erases one dimension of the intersection entirely.

**3. Community-Centered Qualitative Validation** Automated metrics and researcher annotations often miss nuanced visual harms or misinterpret them. Tian et al. emphasizes that evaluations of marginalized groups must involve the impacted communities to understand how representations are actually perceived. Similarly, Mack et al., despite conducting community-centered evaluations on disability, noted that their participant pool lacked older adults, limiting their understanding of age-related harms. A credible intersectional study must incorporate qualitative feedback from older, plus-size individuals to define what constitutes a respectful, realistic representation versus a harmful moralized trope.

**4. Testing the Erasure of Positive Contexts** Warren et al. found that using positive moral prompts resulted in the complete erasure of fat bodies from the generated outputs. An intersectional study must rigorously test whether T2I models are even capable of generating an older, heavier body in a positive moral context without intense prompt engineering, or if the system's safety filters and biases universally block such combinations.

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
