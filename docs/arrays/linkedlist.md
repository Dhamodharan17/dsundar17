# Linked List

## When to Use
- Sequential access, frequent insert/delete
- Cycle detection, reversal, merge
- Clue words: "reverse", "merge", "cycle", "middle", "reorder"

## Templates

### Reverse Linked List
```python
def reverseList(head):
    prev = None
    curr = head
    while curr:
        nxt = curr.next
        curr.next = prev
        prev = curr
        curr = nxt
    return prev
```

### Merge Two Sorted Lists
```python
def mergeTwoLists(l1, l2):
    dummy = ListNode(0)
    curr = dummy
    while l1 and l2:
        if l1.val <= l2.val:
            curr.next = l1
            l1 = l1.next
        else:
            curr.next = l2
            l2 = l2.next
        curr = curr.next
    curr.next = l1 or l2
    return dummy.next
```

### Find Middle (Slow & Fast)
```python
def middleNode(head):
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
    return slow
```

### Reorder List (L0→Ln→L1→Ln-1→...)
```python
def reorderList(head):
    # 1. Find middle
    slow = fast = head
    while fast.next and fast.next.next:
        slow = slow.next
        fast = fast.next.next
    # 2. Reverse second half
    prev, curr = None, slow.next
    slow.next = None
    while curr:
        nxt = curr.next
        curr.next = prev
        prev = curr
        curr = nxt
    # 3. Merge two halves
    first, second = head, prev
    while second:
        tmp1, tmp2 = first.next, second.next
        first.next = second
        second.next = tmp1
        first, second = tmp1, tmp2
```

## Key Problems
| # | Problem | Key Trick |
|---|---------|-----------|
| 1 | Reverse Linked List | prev/curr/next pointers |
| 2 | Merge Two Sorted Lists | Dummy node + compare |
| 3 | Linked List Cycle | Slow & fast pointers |
| 4 | Reorder List | Find mid → reverse → merge |
| 5 | Remove Nth Node From End | Two pointers, n gap |
| 6 | Add Two Numbers | Carry + dummy node |
| 7 | LRU Cache | HashMap + doubly linked list |

## My Notes
<!-- Add your own observations, mistakes, and learnings below -->
