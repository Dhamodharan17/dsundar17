# Intervals

## When to Use
- Merging overlapping intervals
- Inserting into intervals
- Meeting room problems
- Clue words: "interval", "overlap", "merge", "schedule", "meeting"

## Template

### Merge Intervals
```java
Arrays.sort(intervals, (a, b) -> a[0] - b[0]);
List<int[]> merged = new ArrayList<>();
for (int[] interval : intervals) {
    if (merged.isEmpty() || merged.get(merged.size() - 1)[1] < interval[0]) {
        merged.add(interval);
    } else {
        merged.get(merged.size() - 1)[1] = Math.max(merged.get(merged.size() - 1)[1], interval[1]);
    }
}
```

### Insert Interval
```java
List<int[]> result = new ArrayList<>();
int i = 0;
// Add all intervals before newInterval
while (i < intervals.length && intervals[i][1] < newInterval[0]) {
    result.add(intervals[i++]);
}
// Merge overlapping intervals
while (i < intervals.length && intervals[i][0] <= newInterval[1]) {
    newInterval[0] = Math.min(newInterval[0], intervals[i][0]);
    newInterval[1] = Math.max(newInterval[1], intervals[i][1]);
    i++;
}
result.add(newInterval);
// Add remaining
while (i < intervals.length) result.add(intervals[i++]);
```

## Key Problems
| Problem | Approach |
|---------|----------|
| Merge Intervals | Sort by start, merge overlapping |
| Insert Interval | Add before, merge overlap, add after |
| Meeting Rooms | Sort, check no overlap |
| Meeting Rooms II | Min heap on end times |
| Non-overlapping Intervals | Greedy, sort by end, count removals |
