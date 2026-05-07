# Knapsack Pattern

## When to Use
- Choose items with **weight/cost constraint** to maximize/minimize value
- "Can we make sum X from given items?"
- Clue words: "subset sum", "partition", "target sum", "profit", "capacity"

## Variants

| Variant | Items reusable? | Example |
|---|---|---|
| 0/1 Knapsack | No (pick or skip) | Subset Sum, Partition Equal |
| Unbounded Knapsack | Yes (pick unlimited) | Coin Change, Rod Cutting |
| Bounded Knapsack | Limited copies | — |

## Template

### 0/1 Knapsack (Bottom-Up)
```java
int knapsack(int[] weights, int[] values, int capacity) {
    int n = weights.length;
    int[][] dp = new int[n + 1][capacity + 1];

    for (int i = 1; i <= n; i++) {
        for (int w = 0; w <= capacity; w++) {
            dp[i][w] = dp[i - 1][w]; // skip item
            if (weights[i - 1] <= w) {
                dp[i][w] = Math.max(dp[i][w],
                    dp[i - 1][w - weights[i - 1]] + values[i - 1]); // take item
            }
        }
    }
    return dp[n][capacity];
}
```

### Space Optimized (1D array)
```java
int[] dp = new int[capacity + 1];
for (int i = 0; i < n; i++) {
    for (int w = capacity; w >= weights[i]; w--) { // reverse for 0/1
        dp[w] = Math.max(dp[w], dp[w - weights[i]] + values[i]);
    }
}
```

### Unbounded Knapsack (forward loop)
```java
int[] dp = new int[capacity + 1];
for (int i = 0; i < n; i++) {
    for (int w = weights[i]; w <= capacity; w++) { // forward for unbounded
        dp[w] = Math.max(dp[w], dp[w - weights[i]] + values[i]);
    }
}
```

## Key Insight
> **0/1 → reverse inner loop** (each item used once)
> **Unbounded → forward inner loop** (item reused)

## Complexity
- **Time:** O(n × capacity)
- **Space:** O(capacity) with 1D optimization

## Edge Cases
- Capacity = 0
- All items heavier than capacity
- Items with 0 weight

## Problems

| # | Problem | Difficulty | Variant |
|---|---|---|---|
| 1 | Subset Sum | Medium | 0/1 (boolean dp) |
| 2 | Partition Equal Subset Sum | Medium | 0/1 (target = totalSum/2) |
| 3 | Coin Change | Medium | Unbounded (min coins) |
| 4 | Coin Change 2 (count ways) | Medium | Unbounded (count) |
| 5 | Target Sum | Medium | 0/1 (convert to subset sum) |

## My Notes
<!-- Add your own observations, mistakes, and learnings below -->

