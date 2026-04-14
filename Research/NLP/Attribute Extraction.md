Vision API pricing is calculated based on "tiles." A standard 1024x1024 generated image requires 4 tiles plus a base fee, equating to exactly **765 input tokens** per image. The JSON response will be roughly **100 output tokens**.

Here is the cost breakdown for auditing all 1,500 images:

- Input: $2.50 per 1M tokens
- Output: $10.00 per 1M tokens
- Cost per image: ~$0.003
- **Total for 1,500 images: ~$4.50 to $5.50 (approx. ₹380 - ₹460)**
  
#### **Manual Observation:**
1. No black, brown, asian representation
		- **Light Skin:** 80% (32 images)
		- **Medium Skin:** 17.5% (7 images)
	    - **Dark Skin:** 0% (0 images)
    
2. Domain Fallback in Edge-Case Demographics.
		- In all weird profession combinations - eg. Teen waiter, Teen construction worker senior waiter, senior graphic designer - its creating animated images and try to give some humorous perspective. 
		- Although some of these professions are illegal like Teen construction worker, but in 3rd world countries these professions actually exist, but i think the model isn't trained enough for this.
  
3. Almost no hearing aid device in hearing disability people.

4. Environmental Displacement ($\Delta_D$ = Severe):
	- The model generates a "Neutral" professional usually at work. 
	- When disability token is added, it kicks them out of the workplace.

			- Neutral Images: 
					- 75% - Workplace 
					- 0% - Domestic
		    - Conditioned Images:
				    - 43.7% - Workplace.
					- 18.7% - Domestic
					
5. The model is usually creating images of females when there is a caregiving job. No high paying tech jobs have any female representation.

another attribute we can add: animated or not?
reasoning behind choosing any attribute for comparision