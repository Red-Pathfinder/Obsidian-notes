## Maximizing a Function

> Problem: Maximize
> **f(x) = x²**
> where **0 ≤ x ≤ 31**
---
## 🎯 Objective

Goal: Find the value of x (between 0 and 31) that gives the maximum value of f(x) = x² using a Genetic Algorithm.

Since:
- Maximum possible x = **31**
- True optimum = **31² = 961**


Genetic Algorithm will **evolve toward this value step by step**.

---
## 🧩 Step 1: Encoding (Representation)

Encoding Method: Binary Encoding

Range: 0 to 31
To represent 31 in binary:

31 = **11111** → requires **5 bits**

| Decimal | Binary |
| --- | --- |
| 0 | 00000 |
| 31 | 11111 |

Each **5-bit string = one chromosome (solution)**

---

## 👥 Step 2: Initial Population

Population size = 4 (random selection)

Randomly chosen values:

| Chromosome | x   | Binary                     | Fitness f(x)=x² |
| ---------- | --- | -------------------------- | --------------- |
| C1         | 12  | 01100                      | 144             |
| C2         | 25  | 11001                      | 625             |
| C3         | 5   | 00101                      | 25              |
| C4         | 19  | 10011                      | 361             |
|            |     | $$\sum_{i=0}^{i=n}f(x) =$$ | <br>1155        |
|            |     | Avg =                      | 288.75          |
|            |     | Max =                      | 625             |

---
## 📊 Step 3: Selection Probability

Formula:
$$Probability = \frac{f(x)}{\text{Total fitness}}$$

| Chromosome | Fitness | Probability |
| --- | --- | --- |
| C1 | 144 | 0.1247 |
| C2 | 625 | 0.5411 |
| C3 | 25 | 0.0216 |
| C4 | 361 | 0.3126 |

Higher fitness → Higher chance of selection

---
## 🔢 Step 4: Expected Count

Formula:

$$
Expected Count = \frac{f(x)}{\text{Average fitness}}
$$

| Chromosome | Expected | Actual (rounded) |
| --- | --- | --- |
| C1 | 0.50 | 1 |
| C2 | 2.16 | 2 |
| C3 | 0.08 | 0 |
| C4 | 1.25 | 1 |

---
## 🧬 Step 5: Mating Pool

Selected based on actual count

Mating pool (4 chromosomes):
- C1 → once
- C2 → twice
- C4 → once
- C3 → eliminated
---
## 🔀 Step 6: Crossover

Random crossover points selected.
### Example Results (After Crossover)

<table style="border-collapse: collapse; text-align: center; vertical-align: middle; width: 100%; font-family: sans-serif; background-color: #1e1e1e; color: #ffffff; border: 1px solid #444;">
  <thead>
    <tr style="background-color: #333333; color: #ffcc00;">
      <th style="padding: 12px; border: 1px solid #444;">Mating Pool</th>
      <th style="padding: 12px; border: 1px solid #444;">Crossover Point</th>
      <th style="padding: 12px; border: 1px solid #444;">Offspring</th>
      <th style="padding: 12px; border: 1px solid #444;">Result</th>
      <th style="padding: 12px; border: 1px solid #444;">Decimal</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="padding: 15px; border: 1px solid #444;">
        0110<span style="background:#4CAF50; color:#fff; padding:2px 6px; border-radius:4px; margin-left:2px;">0</span>
      </td>
      <td rowspan="2" style="padding: 15px; border: 1px solid #444; font-weight: bold; font-size: 1.2em;">4</td>
      <td style="padding: 15px; border: 1px solid #444;">O1</td>
      <td style="padding: 15px; border: 1px solid #444;">
        0110<span style="background:#2196F3; color:#fff; padding:2px 6px; border-radius:4px; margin-left:2px;">1</span>
      </td>
      <td style="padding: 15px; border: 1px solid #444;">13</td>
    </tr>
    <tr>
      <td style="padding: 15px; border: 1px solid #444;">
        1100<span style="background:#2196F3; color:#fff; padding:2px 6px; border-radius:4px; margin-left:2px;">1</span>
      </td>
      <td style="padding: 15px; border: 1px solid #444;">O2</td>
      <td style="padding: 15px; border: 1px solid #444;">
        1100<span style="background:#4CAF50; color:#fff; padding:2px 6px; border-radius:4px; margin-left:2px;">0</span>
      </td>
      <td style="padding: 15px; border: 1px solid #444;">24</td>
    </tr>

    <tr>
      <td style="padding: 15px; border: 1px solid #444;">
        11<span style="background:#9C27B0; color:#fff; padding:2px 6px; border-radius:4px; margin-left:2px;">001</span>
      </td>
      <td rowspan="2" style="padding: 15px; border: 1px solid #444; font-weight: bold; font-size: 1.2em;">2</td>
      <td style="padding: 15px; border: 1px solid #444;">O3</td>
      <td style="padding: 15px; border: 1px solid #444;">
        11<span style="background:#EF6C00; color:#fff; padding:2px 6px; border-radius:4px; margin-left:2px;">011</span>
      </td>
      <td style="padding: 15px; border: 1px solid #444;">27</td>
    </tr>
    <tr>
      <td style="padding: 15px; border: 1px solid #444;">
        10<span style="background:#EF6C00; color:#fff; padding:2px 6px; border-radius:4px; margin-left:2px;">011</span>
      </td>
      <td style="padding: 15px; border: 1px solid #444;">O4</td>
      <td style="padding: 15px; border: 1px solid #444;">
        10<span style="background:#9C27B0; color:#fff; padding:2px 6px; border-radius:4px; margin-left:2px;">001</span>
      </td>
      <td style="padding: 15px; border: 1px solid #444;">17</td>
    </tr>
  </tbody>
</table>
### Fitness

| x | f(x) |
| --- | --- |
| 13 | 169 |
| 24 | 576 |
| 27 | 729 |
| 17 | 289 |
**New Max = 729**
(previous max = 625)

Crossover improved solution
---
## 🧪 Step 7: Mutation

Purpose:

Adds diversity and prevents premature convergence

Mutation rule: Flip selected bits randomly.

After mutation:

| Binary | Decimal | Fitness |
| --- | --- | --- |
| 11101 | 29 | 841 |
| 11000 | 24 | 576 |
| 11011 | 27 | 729 |
| 10100 | 20 | 400 |
**New Max = 841**

Mutation further improved solution
---
## 🔁 Step 8: Repeat Process

Cycle:
1. Selection
2. Crossover
3. Mutation
4. Evaluate fitness


Repeat until:
- Maximum value reached, OR
- No significant improvement
---
## 📈 Evolution Summary

| Stage | Best Fitness |
| --- | --- |
| Initial | 625 |
| After Crossover | 729 |
| After Mutation | 841 |
| Optimal (expected) | 961 |

Genetic Algorithm gradually **moves toward the optimal solution**.
---
## 🧠 Key Concepts (Quick Revision)
- Chromosome → Binary representation of solution
- Population → Set of solutions
- Fitness → Objective function value
- Selection → Survival of the fittest
- Crossover → Combine parents
- Mutation → Random variation
- Iteration → Evolution over generations
---
## 🌱 Intuition

> Start with random guesses.
> Keep the good ones.
> Mix them.
> Mutate them.
> Repeat.
>
> And slowly… the solution learns to become better.

