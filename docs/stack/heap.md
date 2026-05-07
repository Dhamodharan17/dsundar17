# Heap / Priority Queue

## When to Use
- Top K elements
- Merge K sorted lists
- Running median
- Clue words: "top k", "kth largest", "merge sorted", "median", "schedule"

## Templates

### Top K Frequent Elements
```java
Map<Integer, Integer> freq = new HashMap<>();
for (int num : nums) freq.merge(num, 1, Integer::sum);

PriorityQueue<Integer> minHeap = new PriorityQueue<>((a, b) -> freq.get(a) - freq.get(b));
for (int key : freq.keySet()) {
    minHeap.offer(key);
    if (minHeap.size() > k) minHeap.poll();
}
```

### Kth Largest Element
```java
PriorityQueue<Integer> minHeap = new PriorityQueue<>();
for (int num : nums) {
    minHeap.offer(num);
    if (minHeap.size() > k) minHeap.poll();
}
return minHeap.peek();
```

### Merge K Sorted Lists
```java
PriorityQueue<ListNode> pq = new PriorityQueue<>((a, b) -> a.val - b.val);
for (ListNode list : lists) if (list != null) pq.offer(list);

ListNode dummy = new ListNode(0), curr = dummy;
while (!pq.isEmpty()) {
    ListNode node = pq.poll();
    curr.next = node;
    curr = curr.next;
    if (node.next != null) pq.offer(node.next);
}
return dummy.next;
```

### Running Median (Two Heaps)
```java
PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Collections.reverseOrder()); // lower half
PriorityQueue<Integer> minHeap = new PriorityQueue<>(); // upper half

void addNum(int num) {
    maxHeap.offer(num);
    minHeap.offer(maxHeap.poll());
    if (minHeap.size() > maxHeap.size()) maxHeap.offer(minHeap.poll());
}
double findMedian() {
    return maxHeap.size() > minHeap.size() ? maxHeap.peek() : (maxHeap.peek() + minHeap.peek()) / 2.0;
}
```

## Key Problems
| Problem | Approach |
|---------|----------|
| Kth Largest in Stream | Min heap of size K |
| Top K Frequent Elements | Min heap by frequency |
| Merge K Sorted Lists | Min heap of list heads |
| Find Median from Data Stream | Max heap + Min heap |
| Meeting Rooms II | Min heap on end times |
