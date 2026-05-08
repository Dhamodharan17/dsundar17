# DSA Progress Checker

---

| | | | |
|---|---|---|---|
| ✅ [Two Pointer](arrays/two-pointer.md) | ✅ [Recursion](dp/recursion.md) | ✅ [Stack](stack/stack.md) | [Trie](trees/trie.md) |
| ✅ [Slow & Fast Pointers](arrays/slow-fast-pointers.md) | ✅ [Backtracking](dp/backtracking.md) | ✅ [Heap](stack/heap.md) | [AVL Tree](trees/avl-tree.md) |
| ✅ [Sliding Window](arrays/sliding-window.md) | ✅ [DP](dp/knapsack.md) | ✅ [Deque](stack/deque.md) | [Segment Tree](trees/segment-tree.md) |
| ✅ [Interval](arrays/interval.md) | ✅ [Tree](trees/trees.md) | ✅ [Hashmap](arrays/hashmap.md) | [Fenwick Tree](trees/fenwick-tree.md) |
| ✅ [Prefix Sum](arrays/prefix-sum.md) | ✅ [Graph](trees/graph.md) | ✅ [Matrices](arrays/matrices.md) | [Number Theory](dp/number-theory.md) |
| ✅ [Binary Search](arrays/binary-search.md) | ✅ [Linked List](arrays/linkedlist.md) | | |
| ✅ [Greedy](arrays/greedy.md) | | | |

---

## Notes

- [All DSA Note 800 Page](https://drive.google.com/file/d/1EdAZvzsxeVTX7LTBYG0dXoQwnxBqdQK5/view?usp=sharing)
- [Notion L5](https://www.notion.so/L5-Prep-2b1ab1fe3aaa80009650ddbf30ddae5d)
- [DSA Tracker Sheet](https://docs.google.com/spreadsheets/d/1qGPZ9g5vV1lvvCpVI3QXgEs-KNBc3oGDfKA2rS3iRnk/edit?usp=sharing)
---

<details>
<summary><b>Time Complexity</b></summary>

| | | | | | |
|---|---|---|---|---|---|
| **Data Structure** | **Build** | **Access** | **Search** | **Insert** | **Delete** |
| Array | O(n) | O(1) | O(n) | O(n) | O(n) |
| Stack | O(n) | O(n) | O(n) | O(1) | O(1) |
| Queue / Deque | O(n) | O(n) | O(n) | O(1) | O(1) |
| Linked List | O(n) | O(n) | O(n) | O(1) | O(1) |
| Hash Map | O(n) | — | O(1) | O(1) | O(1) |
| BST (balanced) | O(n log n) | O(log n) | O(log n) | O(log n) | O(log n) |
| BST (worst) | O(n²) | O(n) | O(n) | O(n) | O(n) |
| AVL / Red-Black | O(n log n) | O(log n) | O(log n) | O(log n) | O(log n) |
| Heap | O(n) | — | O(n) | O(log n) | O(log n) |
| Trie | O(n·k) | — | O(k) | O(k) | O(k) |
| Segment Tree | O(n) | — | O(log n) | O(log n) | O(log n) |
| Fenwick Tree | O(n) | — | O(log n) | O(log n) | O(log n) |
| Graph (adj list) | O(V+E) | — | O(V+E) | O(1) | O(E) |

> k = length of key/word
> Heap search is O(n) — only root (min/max) is guaranteed, no sorted order among siblings, must scan all elements

</details>

---

<details>
<summary><b>Technique Complexity</b></summary>

| | | | |
|---|---|---|---|
| **Technique** | **Time** | **Space** | **Use** |
| Two Pointer | O(n) | O(1) | Sorted array, pair sum, remove duplicates |
| Sliding Window | O(n) | O(1) or O(k) | Subarray of fixed/variable size |
| Prefix Sum | O(n) build, O(1) query | O(n) | Range sum queries |
| Binary Search | O(log n) | O(1) | Sorted data, search on answer |
| Monotonic Stack | O(n) | O(n) | Next/Prev Greater/Smaller element |
| Greedy | O(n log n) | O(1) | Interval scheduling, activity selection |
| Backtracking | O(2ⁿ) or O(n!) | O(n) | Permutations, subsets, N-Queens |
| BFS | O(V+E) | O(V) | Shortest path (unweighted), level order |
| DFS | O(V+E) | O(V) | Path finding, cycle detection, topo sort |
| Dijkstra | O((V+E) log V) | O(V) | Shortest path (weighted, no -ve) |
| Bellman-Ford | O(V·E) | O(V) | Shortest path (with -ve edges) |
| Floyd-Warshall | O(V³) | O(V²) | All-pairs shortest path |
| Kruskal | O(E log E) | O(V) | MST (edge list + DSU) |
| Prim | O((V+E) log V) | O(V) | MST (adj list + heap) |
| Topological Sort | O(V+E) | O(V) | DAG ordering, dependencies |
| DSU (Union-Find) | O(α(n)) per op | O(n) | Connected components, grouping |
| DP (1D) | O(n) | O(n) | Fibonacci, climbing stairs |
| DP (2D) | O(n·m) | O(n·m) | Knapsack, LCS, grid paths |

</details>