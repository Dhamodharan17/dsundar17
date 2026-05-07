# Two Pointer

## When to Use
- Sorted array problems
- Finding pairs/triplets with a target sum
- Removing duplicates in-place
- Partitioning (Dutch National Flag)
- Clue words: "pair", "sorted", "in-place", "two sum", "three sum"

## Template

### Opposite Direction (sorted array)
```java
int left = 0, right = nums.length - 1;
while (left < right) {
    int sum = nums[left] + nums[right];
    if (sum == target) {
        // found
        left++; right--;
    } else if (sum < target) {
        left++;
    } else {
        right--;
    }
}
```

### Same Direction (fast & slow)
```java
int slow = 0;
for (int fast = 0; fast < nums.length; fast++) {
    if (/* condition */) {
        nums[slow] = nums[fast];
        slow++;
    }
}
// slow = new length
```

## Complexity
- **Time:** O(n) for two pointers, O(n²) for 3Sum
- **Space:** O(1)

## Edge Cases
- Array with < 2 elements
- All elements same
- Negative numbers (for sum problems)
- Duplicates — skip with `while (left < right && nums[left] == nums[left-1]) left++`

## Problems

| # | Problem | Difficulty | Key Trick |
|---|---|---|---|
| 1 | Two Sum II (sorted) | Easy | Opposite pointers |
| 2 | Remove Duplicates from Sorted Array | Easy | Fast-slow pointer |
| 3 | 3Sum | Medium | Fix one + two pointer |
| 4 | Container With Most Water | Medium | Move shorter side inward |
| 5 | Trapping Rain Water | Hard | Left/right max tracking |

## My Notes
<!-- Add your own observations, mistakes, and learnings below -->

