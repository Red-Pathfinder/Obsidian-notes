**Tags:** #paper #diffusion-models #bias #fairness #AI #deep-learning 

#ComputerVision  #causal-inference
**Paper Link/Code:** [github.com/FanQi-AI/Debias](https://github.com/FanQi-AI/Debias)

---

## 1. The Core Problem: Fixing the "Technical Debt"

> [!bug] The Issue
> [[Text-to-Image (T2I)]] models like [[Stable Diffusion]] have inherent demographic biases (e.g., prompting "CEO" consistently generates a specific demographic).

> [!fail] Prior Work's Flaw
> Older methods treated this like a documentation error—they tried to fix it by tweaking the [[text encoder]] or wrapping the prompt in new instructions ([[prompt engineering]]).

> [!success] This Paper's Argument
> The bias isn't in the prompt; it's a hard-coded logic error deep inside the [[U-Net architecture]]. We need to debug the [[U-Net]] itself.

<br>

---

## 2. The Solution: [[Surgical Fine-Tuning]]

* **[[Causal Analysis]]:** Instead of retraining the entire model (millions of parameters), the authors use [[causal analysis]] to find the exact "faulty wires" (neurons) responsible for the bias.

* **Hardware & Compute Efficiency:** By isolating the specific neurons, this method only modifies ==~0.2M parameters==. 
<br>

---

## 3. The Bias Detector: [[Contrast Neuron Sensitivity Metric (CNSM)]]

The CNSM acts as a "profiler" or unit test to find which neurons are hard-coding the bias.

> [!quote] The Math & Logic
> It functions like a [[partial derivative]] or [[sensitivity analysis]]. 
> $$CNSM_i = \left| \frac{\partial \text{output}}{\partial \text{attribute}_{\text{target}}} \right|$$

<br>

### 🛠️ How it works:
1. **Input** a base prompt (e.g., "A photo of a doctor").
2. **Swap** the demographic attribute ("man" vs. "woman") while keeping the random seed identical.
3. **Measure** the activation values of every U-Net neuron.

<br>

### 📊 Interpretation:
* **High $CNSM$ (closer to 1.0):** The neuron reacts wildly to the gender swap. It is heavily biased and flagged for fine-tuning.
* **Low $CNSM$ (e.g., 0.0001):** The neuron doesn't care about the demographic swap. It is a "fair" neuron and is left completely frozen to maintain model stability.

<br>

### 📍 Location:
Biased neurons are predominantly found in the **[[cross-attention layers]]** (like `attn2`), specifically on the **[[Decoder]]** (upsampling) side of the U-Net, because that is where visual concepts and pixels are physically reconstructed.

<br>

---

## 4. The Implementation: Dual-Loss Fine-Tuning

Once the biased neurons are isolated, they are updated using two competing [[loss functions]]:

> [!example] A. [[Distribution Loss]]
> **Purpose:** Forces the model's output to hit a specific demographic target.

> [!example] B. [[Semantic Loss]] ($\mathcal{L}_{sem}$)
> **Purpose:** The "Regression Test." It ensures that while fixing the bias, the core concept remains intact (i.e., the doctor still looks like a doctor, not a blurry mess).
> 
> **The Math:** It calculates the distance between the [[feature maps]] of the original model and the debiased model.
> $$\mathcal{L}_{sem} = \| \phi_{orig}(x) - \phi_{new}(x) \|^2$$
> 
> **Key Detail:** We compare the **[[hidden layers]]** ([[feature maps]], $\phi$) of the U-Net, *not* the raw pixels. Comparing raw pixels is too literal. Feature maps capture the actual *meaning* or semantics.

<br>

---

## 5. Deployment Flexibility: Absolute vs. Relative Fairness

*  **[[Absolute Fairness]]:** Forcing an exact 50/50 split (e.g., 50% Male / 50% Female).
*  **[[Relative Fairness]]:** Adjusting the model to reflect a specific, custom demographic ratio (e.g., 80% elderly / 20% young). This is highly useful for tailoring AI to specific regional populations.

<br>

---

## 6. Conceptual [[PyTorch]] Implementation

```python
import torch

# 1. Identify Biased Neurons (High CNSM)
biased_indices = [12, 45, 102, 550] 

# 2. Freeze the entire U-Net (Millions of parameters)
for param in unet.parameters():
    param.requires_grad = False

# 3. Surgical Intervention: Unfreeze ONLY the highly sensitive attn2 layers
for name, param in unet.named_parameters():
    if "attn2" in name: 
        param.requires_grad = True # Treat as sparse fine-tuning

# 4. Apply Dual Loss Function
def total_loss(output, target_dist, original_features):
    L_dist = distribution_loss(output, target_dist) # Pushes to demographic target
    L_sem = semantic_loss(output, original_features) # Preserves 'doctor-ness'
    return L_dist + (lambda_weight * L_sem)
```