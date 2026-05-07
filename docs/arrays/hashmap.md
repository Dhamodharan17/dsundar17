# HashMap

## When to Use
- Frequency counting
- Two Sum type lookups
- Grouping / anagram detection
- Clue words: "frequency", "count", "group", "anagram", "two sum"

## Templates

### Two Sum
```java
Map<Integer, Integer> map = new HashMap<>();
for (int i = 0; i < nums.length; i++) {
    int complement = target - nums[i];
    if (map.containsKey(complement)) return new int[]{map.get(complement), i};
    map.put(nums[i], i);
}
```

### Group Anagrams
```java
Map<String, List<String>> map = new HashMap<>();
for (String s : strs) {
    char[] chars = s.toCharArray();
    Arrays.sort(chars);
    String key = new String(chars);
    map.computeIfAbsent(key, k -> new ArrayList<>()).add(s);
}
return new ArrayList<>(map.values());
```

### Frequency Count
```java
Map<Integer, Integer> freq = new HashMap<>();
for (int num : nums) freq.merge(num, 1, Integer::sum);
```

### Longest Consecutive Sequence
```java
Set<Integer> set = new HashSet<>(Arrays.asList(/* nums boxed */));
int longest = 0;
for (int num : set) {
    if (!set.contains(num - 1)) { // start of sequence
        int length = 1;
        while (set.contains(num + length)) length++;
        longest = Math.max(longest, length);
    }
}
```

## Key Problems
| Problem | Approach |
|---------|----------|
| Two Sum | Map value → index |
| Group Anagrams | Sorted string as key |
| Longest Consecutive Sequence | HashSet, find sequence starts |
| Top K Frequent Elements | Frequency map + heap |
| LRU Cache | HashMap + Doubly Linked List |
