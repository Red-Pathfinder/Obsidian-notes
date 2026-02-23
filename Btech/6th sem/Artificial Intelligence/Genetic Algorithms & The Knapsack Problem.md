### The Core Idea

You can simulate **natural evolution** on a computer to solve very hard optimization problems.

Some problems:
- Have **too many possible combinations**
- Are **too slow** to solve by brute force
- Need a **good solution quickly**, even if it’s not perfectly optimal


Genetic Algorithms (GA) help find **near-optimal solutions efficiently**.
---
## The Example: Knapsack Problem
### Problem Statement

You are going on a trip.
- Your backpack capacity = **3 kg**
- You have several items
- Each item has:

    - Weight

    - Value


![00:01:35](screenshot-01KJ4ZFJMK14RPTMNGNWAXY58A.png)
[00:01:35](https://www.youtube.com/watch?v=uQj5UNhCPuo&t=95.620072s)

Goal:

> Choose the combination of items that gives **maximum value** without exceeding the weight limit.
---
### Brute Force Approach

Try **every possible combination**.

If there are **n items**:
- Total combinations = **2ⁿ**


Problem:
- Time grows **exponentially**
- Example:

    - 5 items → manageable

    - 15 items → \~1 million combinations

    - 70 items → impossible to compute in reasonable time


This exponential explosion makes brute force impractical.
---
## What is the Knapsack Problem (Theory)

The knapsack problem asks:

> Is there a subset of items whose total weight is within the limit and whose total value is maximum?

It belongs to the class of **NP-hard / NP-complete** optimization problems.

Meaning:
- No known fast exact solution for large inputs
- We often rely on **approximation methods**
---
## Genetic Algorithms (GA)
### Inspiration

Genetic Algorithms simulate:
- Evolution
- Natural selection
- Survival of the fittest


They **search the solution space intelligently** instead of checking everything.

Used when:
- Exact calculation is too expensive
- Search space is huge
- Approximate solutions are acceptable
---
## Representation of a Solution

Each possible solution is encoded as a **binary string**.

Example:

Items: [Laptop, Coffee Maker, Jacket, Phone]

Solution: 1010
Meaning:
1 → include item
0 → exclude item

Each binary string = **one candidate solution (individual)**.
---
## Step 1: Initial Population

Generate a **population** of random solutions.

Example:
- 100 random binary strings
- Each represents a different item combination


This is the starting generation.
---
## Step 2: Fitness Function

The fitness function evaluates how good a solution is.

For Knapsack:
- If weight > limit → fitness = 0 (invalid)
- Otherwise:


Fitness = total value of selected items

Higher fitness = better solution.
---
## Step 3: Selection

Select the **best individuals** based on fitness.

Idea:

> Better solutions are more likely to reproduce.

Methods may include:
- Roulette selection
- Tournament selection
- Keeping top performers (elitism)
---
## Step 4: Crossover (Reproduction)

Create new solutions by combining two parents.
**Single-point crossover:**

Parent A: 101|011
Parent B: 010|110

Child: 101110

This mixes good traits from both parents.
---
## Step 5: Elitism (Important)

Problem:
- Good solutions may disappear randomly


Solution:
- Copy the **best individuals directly** into the next generation


This ensures progress doesn’t get lost.
---
## Step 6: Mutation

To maintain diversity:
- Randomly flip bits with small probability (\~5%)


Example:

Before: 101010
After : 101110

Purpose:
- Explore new areas of the search space
- Avoid getting stuck in local optima
---
## Step 7: Iteration

Repeat:
1. Evaluate fitness
2. Select parents
3. Crossover
4. Mutation
5. Create next generation


Stop when:
- Max generations reached, OR
- Solution quality is good enough
---
## Summary of Genetic Algorithm Components

Every GA needs:
1. **Representation** of solution
2. **Population initialization**
3. **Fitness function**
4. **Selection method**
5. **Crossover**
6. **Mutation**
7. **Stopping condition**
---
## Performance Results (From Example)

Observations:
- For small item counts → GA behaves almost random
- For \~30 items:

    - GA finds optimal solution in \~0.025 seconds

    - Brute force takes \~1 second

    - \~40x faster


For very large problems:
- Example: 77 items
- GA achieved:

    - \~97.5% accuracy quickly

    - With more generations → up to \~99%


Important insight:

> GA time grows slowly compared to exponential brute force.
---
## When Genetic Algorithms Work Well

Good for:
- Large combinatorial problems
- Scheduling problems
- Routing problems
- Optimization without clear formulas
- Search spaces too big for brute force


Also used in:
- Game strategies
- Engineering design
- Machine learning optimization
- Simulation of evolution
---
## Limitations
1. **No guarantee of perfect solution**


    - Only near-optimal
2. **Fitness function cost**


    - If evaluating fitness is slow → GA becomes slow
3. **Parameter tuning needed**


    - Population size

    - Mutation rate

    - Number of generations
---
## Key Intuition

Brute force:

> Try everything.

Genetic Algorithm:

> Try many guesses → keep the good ones → mix them → slightly mutate → repeat → gradually evolve a strong solution.

Evolution, but for optimization.