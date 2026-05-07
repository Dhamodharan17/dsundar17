# Sliding Window

## When to Use
- Subarray / substring problems with a **condition** (max/min length, sum ≥ k, at most k distinct)
- Contiguous elements only
- Clue words: "subarray", "substring", "window", "consecutive"

## Template

### Fixed Size Window
```java
for (int i = 0; i < nums.length; i++) {
    // add nums[i] to window
    if (i >= k - 1) {
        // record answer
        // remove nums[i - k + 1] from window
    }
}
```

### Variable Size Window
```java
int left = 0;
for (int right = 0; right < nums.length; right++) {
    // expand: add nums[right] to window

    while (/* window condition breaks */) {
        // shrink: remove nums[left] from window
        left++;
    }
    // record answer (max/min window size = right - left + 1)
}
```

## Complexity
- **Time:** O(n) — each element enters and leaves window once
- **Space:** O(1) or O(k) if using a map/set

## Edge Cases
- Empty array
- Window size > array length
- All elements same
- Entire array is the answer

## Problems

| # | Problem | Difficulty | Key Trick |
|---|---|---|---|
| 1 | Max Sum Subarray of Size K | Easy | Fixed window |
| 2 | Longest Substring Without Repeating Chars | Medium | HashSet + variable window |
| 3 | Minimum Size Subarray Sum | Medium | Variable window, shrink when sum ≥ target |
| 4 | Longest Repeating Character Replacement | Medium | Track maxFreq, shrink when window - maxFreq > k |
| 5 | Minimum Window Substring | Hard | Two maps, track "formed" count |

## My Notes
<!-- Add your own observations, mistakes, and learnings below -->

