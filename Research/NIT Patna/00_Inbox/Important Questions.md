### Q1
Warren generated:
```
4000 images
```
Do we actually need 4000?
Or can we justify a smaller sample?
Why?
- Important Observation: Some img weren't generated due to safety refusal but were able to be generated when the script was re-executed.

---

### Q2

Warren used:
```
4 human raters
```
We don't have that.
What risks appear if we replace humans with GPT-4o?
List at least 3.
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

Do we need identical percentages?

Or something weaker?