# Prefix Sum

## When to Use
- Range sum queries
- Subarray sum equals K
- Finding equilibrium index
- Clue words: "subarray sum", "range sum", "cumulative", "running total"

## Template

### Build Prefix Sum
```java
int[] prefix = new int[nums.length + 1];
for (int i = 0; i < nums.length; i++) {
    prefix[i + 1] = prefix[i] + nums[i];
}
// Sum of nums[l..r] = prefix[r+1] - prefix[l]
```

### Subarray Sum Equals K (HashMap approach)
```java
int count = 0, sum = 0;
Map<Integer, Integer> map = new HashMap<>();
map.put(0, 1);
for (int num : nums) {
    sum += num;
    count += map.getOrDefault(sum - k, 0);
    map.merge(sum, 1, Integer::sum);
}
return count;
```

### 2D Prefix Sum
```java
int[][] prefix = new int[m + 1][n + 1];
for (int i = 1; i <= m; i++) {
    for (int j = 1; j <= n; j++) {
        prefix[i][j] = matrix[i-1][j-1] + prefix[i-1][j] + prefix[i][j-1] - prefix[i-1][j-1];
    }
}
// Sum of submatrix (r1,c1) to (r2,c2):
// prefix[r2+1][c2+1] - prefix[r1][c2+1] - prefix[r2+1][c1] + prefix[r1][c1]
```

## Key Problems
| Problem | Approach |
|---------|----------|
| Range Sum Query | Prefix array, O(1) per query |
| Subarray Sum Equals K | Prefix + HashMap |
| Contiguous Array | Convert 0→-1, prefix sum + map |
| Product of Array Except Self | Prefix & suffix products |
| 2D Range Sum | 2D prefix sum with inclusion-exclusion |
