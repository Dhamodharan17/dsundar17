# Slow & Fast Pointers

## When to Use
- Cycle detection in linked list
- Finding middle of linked list
- Finding start of cycle
- Clue words: "cycle", "circular", "middle node", "happy number"

## Template

### Cycle Detection (Floyd's Algorithm)
```java
ListNode slow = head, fast = head;
while (fast != null && fast.next != null) {
    slow = slow.next;
    fast = fast.next.next;
    if (slow == fast) return true; // cycle exists
}
return false;
```

### Find Middle of Linked List
```java
ListNode slow = head, fast = head;
while (fast != null && fast.next != null) {
    slow = slow.next;
    fast = fast.next.next;
}
return slow; // middle node
```

### Find Cycle Start
```java
ListNode slow = head, fast = head;
while (fast != null && fast.next != null) {
    slow = slow.next;
    fast = fast.next.next;
    if (slow == fast) {
        slow = head;
        while (slow != fast) {
            slow = slow.next;
            fast = fast.next;
        }
        return slow; // cycle start
    }
}
return null;
```

## Key Problems
| Problem | Approach |
|---------|----------|
| Linked List Cycle | Fast catches slow → cycle |
| Linked List Cycle II | Reset slow to head, move both by 1 |
| Find Middle | Fast reaches end → slow at middle |
| Happy Number | Treat as cycle detection |
| Palindrome Linked List | Find middle → reverse second half → compare |
