# Greedy

## When to Use
- Locally optimal → globally optimal
- Activity selection / scheduling
- Huffman coding, interval problems
- Clue words: "minimum cost", "maximum profit", "schedule", "optimal"

## Template

### Interval Scheduling (max non-overlapping)
```java
Arrays.sort(intervals, (a, b) -> a[1] - b[1]); // sort by end
int count = 1, end = intervals[0][1];
for (int i = 1; i < intervals.length; i++) {
    if (intervals[i][0] >= end) {
        count++;
        end = intervals[i][1];
    }
}
return count;
```

### Jump Game
```java
int farthest = 0;
for (int i = 0; i < nums.length; i++) {
    if (i > farthest) return false;
    farthest = Math.max(farthest, i + nums[i]);
}
return true;
```

### Gas Station
```java
int totalSurplus = 0, currentSurplus = 0, start = 0;
for (int i = 0; i < gas.length; i++) {
    totalSurplus += gas[i] - cost[i];
    currentSurplus += gas[i] - cost[i];
    if (currentSurplus < 0) {
        start = i + 1;
        currentSurplus = 0;
    }
}
return totalSurplus >= 0 ? start : -1;
```

## Key Problems
| Problem | Approach |
|---------|----------|
| Jump Game | Track farthest reachable |
| Jump Game II | BFS-like greedy |
| Gas Station | Track surplus, reset on negative |
| Task Scheduler | Most frequent task first |
| Assign Cookies | Sort both, match smallest |
