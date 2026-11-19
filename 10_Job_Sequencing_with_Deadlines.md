# Job Sequencing with Deadlines (Greedy)

## Theory
* **Problem:** Given `n` jobs, each taking **1 unit of time**, with a deadline `d[i]` and profit `p[i]`. Only one job can run at a time. Maximize total profit by completing jobs on or before their deadlines.
* **Greedy Strategy:** Sort jobs in **descending order of profit**. For each job, assign it to the **latest possible free time slot** `t <= d[i]`. Scheduling as late as possible keeps earlier slots open for jobs with tighter deadlines.

## Algorithm
```text
JobSequencing(jobs, n):
  Sort jobs in descending order of profit
  maxD = maximum deadline among all jobs
  Create slot[1..maxD] initialized to -1 (empty)
  totalProfit = 0

  for i = 1 to n:
    for t = min(maxD, jobs[i].deadline) down to 1:
      if slot[t] == -1:
        slot[t] = jobs[i].id
        totalProfit += jobs[i].profit
        break
  return totalProfit
```

## Complexity
* **Time Complexity:** `O(n^2)` *(sorting takes `O(n log n)`, slot search takes up to `O(n * maxD)`)*
* **Space Complexity:** `O(maxD)` for the slot array.
