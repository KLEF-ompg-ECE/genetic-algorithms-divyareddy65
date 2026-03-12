# Assignment 2 — Genetic Algorithm: Knapsack Problem
## Observation Report

**Student Name  :** M. Divya Reddy  
**Student ID    :** 2310040065
**Date Submitted:** 12 March 2026  

---

## How to Submit

1. Run each experiment following the instructions below
2. Fill in every answer box — do not leave placeholders
3. Make sure the `plots/` folder contains all required images
4. Commit this README and the `plots/` folder to your GitHub repo

---

## Before You Begin — Read the Code

Open `ga_knapsack.py` and read through it. Then answer these questions.

**Q1. What does the `fitness()` function return? Why does an overweight solution score 0?**

```
The fitness() function calculates the total value of the items selected in the knapsack. 
If the total weight exceeds the maximum weight limit, the function returns 0. 
This ensures that overweight solutions are considered invalid and not selected. 
```

**Q2. What does `tournament_select()` do? Why are higher-fitness individuals more likely to be chosen?**

```
The tournament_select() function randomly selects a few individuals from the population and chooses the one with the highest fitness. 
Individuals with higher fitness have a greater chance of winning the tournament. 
This helps the algorithm keep better solutions in the population.
```

**Q3. Look at the `run_ga()` loop. Find this line:**
```python
next_gen = [best_chromosome[:]]
```
**What is this doing? Why is it important to always keep the best solution?**

```
The line next_gen = [best_chromosome[:]] copies the best solution from the current generation into the next generation. 
This is called elitism. 
It ensures that the best solution found so far is not lost during crossover or mutation.
```

---

## Experiment 1 — Baseline Run

**Instructions:** Run the program without changing anything.
```bash
python ga_knapsack.py
```

**Fill in this table:**

| Metric | Your result |
|--------|-------------|
| Number of generations |50 |
| Best value at generation 1 |60 |
| Final best value |77 |
| Total weight of best solution (kg) |14.4 kg |
| Is solution valid (Yes / No) |Yes |

**Copy the printed packing list here:**
```
Water bottle
First aid kit
Sleeping bag
Torch
Energy bars (x6)
Rain jacket
Map & compass
Cooking stove
Rope (10 m)
Sunscreen
Power bank
```

**Look at `plots/experiment_1.png` and describe what you see (2–3 sentences).**  
*Where does the biggest improvement happen? Does the curve flatten at some point?*
```
The graph shows that the fitness value increases quickly during the early generations. 
Most improvements happen in the first few generations as better solutions are found. 
Later the curve becomes flat, showing that the algorithm converges to a stable solution.
```

---

## Experiment 2 — Effect of Mutation Rate

**Instructions:** In `ga_knapsack.py`, find the `# EXPERIMENT 2` block in `__main__`.  
Copy it three times and run with `mutation_rate` = **0.01**, **0.05**, and **0.30**.  
Save plots as `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`.

**Results table:**

| mutation_rate | Final best value | Weight (kg) | Valid? | Shape of curve |
|--------------|-----------------|-------------|--------|------------------|
| 0.01         |  75             |   14.9 Kg   | Yes    | Slow improvement |
| 0.05         |  77             |   14.4 kg   | Yes    |Smooth convergence|
| 0.30         |  78             |   14.1 kg   | Yes    |  Fluctuating     |

**Compare the three plots. What happens when mutation is too low? Too high? (3–4 sentences)**  
*Hint: Too low = no diversity, may get stuck. Too high = random search. What is the sweet spot?*
```
When the mutation rate is very low (0.01), the algorithm explores fewer new solutions and may get stuck. 
A moderate mutation rate (0.05) provides a good balance between exploration and improvement. 
A very high mutation rate (0.30) increases randomness, which can sometimes find better solutions but may also disturb good solutions.
```

**Which mutation_rate gave the best result? Why do you think that is?**
```
The mutation rate of 0.30 produced the highest final value of 78. 
This higher mutation rate allowed the algorithm to explore more combinations and discover a slightly better solution.
```

---

## Summary

**Complete this table with your best result from each experiment:**

| Experiment | Key setting | Final value | Main finding in one sentence |
|------------|-------------|-------------|------------------------------|
| 1 — Baseline | mutation_rate = 0.05 |77 |Balanced mutation gives good convergence |
| 2 — Mutation rate | mutation_rate = 0.30 |78 |Higher mutation explored better solutions |

**In your own words — what is the most important thing you learned about Genetic Algorithms from these experiments? (3–5 sentences)**
```
From this experiment I learned that mutation rate is an important parameter in genetic algorithms. 
A very low mutation rate reduces diversity and may cause the algorithm to get stuck in local solutions. 
A balanced mutation rate allows good exploration and steady improvement. 
A higher mutation rate increases randomness but can sometimes discover better solutions.
```

---

## Submission Checklist

- [ ] Student name and ID filled in
- [ ] Q1, Q2, Q3 answered
- [ ] Experiment 1: table filled, packing list pasted, plot observation written
- [ ] Experiment 2: results table filled (3 rows), observation and answer written
- [ ] Summary table completed and reflection written
- [ ] `plots/` contains: `experiment_1.png`, `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`
