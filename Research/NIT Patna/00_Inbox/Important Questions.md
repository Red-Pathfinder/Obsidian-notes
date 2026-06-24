### Q1
Warren generated:
```
4000 images
```
Do we actually need 4000? - may be not because of funding issues and how less time we have
Or can we justify a smaller sample? - i have no idea
Why?
- Important Observation: Some img weren't generated due to safety refusal but were able to be generated when the script was re-executed.

---

### Q2

Warren used:
```
4 human raters
What risks appear if we replace humans with GPT-4o?```
We don't have that.
List at least 3.
	- VLMs often hallucinate and mark people incorrectly.
	- Inorder to find which img has been marked correctly or incorrectly is hard
```

- When multiple people were generated in an img then a distinct weight label was given to them. Not sure what exactly?
---

### Q3

The paper's biggest limitation was:
```
Only DALL-E 3```

If we test:```
FLUX 
SDXL
```
What would count as a meaningful replication?
	- Flux? as it is a newer model
Do we need identical percentages?
Or something weaker?