https://pricepertoken.com/ to track live API prices
![[Pasted image 20260311203542.png]]![[Pasted image 20260311203702.png]]![[Pasted image 20260311203742.png]]
gemini 2.5 flash per 100 images generated  = $3.9
 - ques:
	 1. How many models req to compare?
	 2. resolution?
	 3. Budget?
	 4. batch / standard
	
<table border="1" cellpadding="8" cellspacing="0">
<thead>
<tr>
<th>Provider</th>
<th>Model</th>
<th>Price (Standard)</th>
<th>Research Suitability</th>
</tr>
</thead>

<tbody>
<tr>
<td>Google</td>
<td>Imagen 4 Standard</td>
<td>$4.00</td>
<td>Good for testing safety filters and enterprise guardrails</td>
</tr>

<tr>
<td>Google</td>
<td>Gemini 3 Pro Image</td>
<td>$13.40</td>
<td>High complexity; excellent for testing nuanced social bias</td>
</tr>

<tr>
<td>OpenAI</td>
<td>GPT Image 1.5 (High)</td>
<td>$17.00</td>
<td>Best for testing state-of-the-art prompt adherence vs bias</td>
</tr>

<tr>
<td>OpenAI</td>
<td>DALL·E 3</td>
<td>$4.00</td>
<td>Reliable baseline for historical bias comparison</td>
</tr>

<tr>
<td>OpenAI</td>
<td>GPT Image 1 Mini</td>
<td>$0.50</td>
<td>Cheapest option for large-scale datasets (1000+ images)</td>
</tr>

<tr>
<td>Stability AI</td>
<td>Stable Diffusion 3.5</td>
<td>$1.00 – $3.00</td>
<td>Best for research. Highly customizable and open-weights</td>
</tr>

</tbody>
</table>
- pair based
- what about  mitigation techniques?
- Do we see the drift visually or we calculate it mathematically
- do we tell u the exact prices for models that are reasonable?
- **is professional spectrum parameters enough? or we delete or remove something?**