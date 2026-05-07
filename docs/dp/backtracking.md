# Backtracking

## When to Use
- Generate all valid combinations/permutations
- Constraint satisfaction (Sudoku, N-Queens)
- Path finding with constraints
- Clue words: "all possible", "generate", "combinations", "permutations"

## Template

### Subsets
```java
void backtrack(int[] nums, int start, List<Integer> current, List<List<Integer>> result) {
    result.add(new ArrayList<>(current));
    for (int i = start; i < nums.length; i++) {
        current.add(nums[i]);
        backtrack(nums, i + 1, current, result);
        current.remove(current.size() - 1); // undo
    }
}
```

### Permutations
```java
void backtrack(int[] nums, boolean[] used, List<Integer> current, List<List<Integer>> result) {
    if (current.size() == nums.length) {
        result.add(new ArrayList<>(current));
        return;
    }
    for (int i = 0; i < nums.length; i++) {
        if (used[i]) continue;
        used[i] = true;
        current.add(nums[i]);
        backtrack(nums, used, current, result);
        current.remove(current.size() - 1);
        used[i] = false;
    }
}
```

### Combination Sum
```java
void backtrack(int[] candidates, int target, int start, List<Integer> current, List<List<Integer>> result) {
    if (target == 0) { result.add(new ArrayList<>(current)); return; }
    for (int i = start; i < candidates.length; i++) {
        if (candidates[i] > target) break;
        current.add(candidates[i]);
        backtrack(candidates, target - candidates[i], i, current, result); // i not i+1 for reuse
        current.remove(current.size() - 1);
    }
}
```

## Key Concepts
- **Choose → Explore → Unchoose** pattern
- Pruning: skip invalid states early to reduce search space
- For duplicates: sort array + `if (i > start && nums[i] == nums[i-1]) continue;`

## Key Problems
| Problem | Approach |
|---------|----------|
| Subsets | Include/exclude each element |
| Permutations | Use visited array |
| N-Queens | Row by row, validate column/diagonal |
| Sudoku Solver | Cell by cell, try 1-9 |
| Word Search | DFS on grid with backtracking |
