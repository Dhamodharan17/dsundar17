# Binary Search

## When to Use
- Sorted array search
- Search space reduction
- Finding boundaries (first/last occurrence)
- Clue words: "sorted", "minimum/maximum that satisfies", "search", "rotated"

## Template

### Standard Binary Search
```java
int lo = 0, hi = nums.length - 1;
while (lo <= hi) {
    int mid = lo + (hi - lo) / 2;
    if (nums[mid] == target) return mid;
    else if (nums[mid] < target) lo = mid + 1;
    else hi = mid - 1;
}
return -1;
```

### Lower Bound (first >= target)
```java
int lo = 0, hi = nums.length;
while (lo < hi) {
    int mid = lo + (hi - lo) / 2;
    if (nums[mid] < target) lo = mid + 1;
    else hi = mid;
}
return lo;
```

### Binary Search on Answer
```java
int lo = minAnswer, hi = maxAnswer;
while (lo < hi) {
    int mid = lo + (hi - lo) / 2;
    if (feasible(mid)) hi = mid;
    else lo = mid + 1;
}
return lo;
```

### Rotated Sorted Array
```java
int lo = 0, hi = nums.length - 1;
while (lo <= hi) {
    int mid = lo + (hi - lo) / 2;
    if (nums[mid] == target) return mid;
    if (nums[lo] <= nums[mid]) { // left half sorted
        if (nums[lo] <= target && target < nums[mid]) hi = mid - 1;
        else lo = mid + 1;
    } else { // right half sorted
        if (nums[mid] < target && target <= nums[hi]) lo = mid + 1;
        else hi = mid - 1;
    }
}
return -1;
```

## Key Problems
| Problem | Approach |
|---------|----------|
| Search in Rotated Array | Check which half is sorted |
| Find Peak Element | Move toward larger neighbor |
| Koko Eating Bananas | Binary search on answer |
| Median of Two Sorted Arrays | Binary search on partition |
| Search a 2D Matrix | Treat as 1D sorted array |
