# BFS & DFS (Trees & Graphs)

## When to Use

| Use BFS | Use DFS |
|---|---|
| Shortest path (unweighted) | Path existence |
| Level-order traversal | Preorder / Inorder / Postorder |
| Nearest neighbor | Detecting cycles |
| Minimum depth | Backtracking problems |

## Template

### BFS (Level Order)
```java
Queue<TreeNode> queue = new LinkedList<>();
queue.offer(root);
while (!queue.isEmpty()) {
    int size = queue.size(); // nodes at current level
    for (int i = 0; i < size; i++) {
        TreeNode node = queue.poll();
        // process node
        if (node.left != null) queue.offer(node.left);
        if (node.right != null) queue.offer(node.right);
    }
}
```

### DFS (Recursive)
```java
void dfs(TreeNode node) {
    if (node == null) return;
    // preorder: process here
    dfs(node.left);
    // inorder: process here
    dfs(node.right);
    // postorder: process here
}
```

### DFS (Iterative with Stack)
```java
Stack<TreeNode> stack = new Stack<>();
stack.push(root);
while (!stack.isEmpty()) {
    TreeNode node = stack.pop();
    // process node
    if (node.right != null) stack.push(node.right); // right first
    if (node.left != null) stack.push(node.left);
}
```

## Traversal Order Cheat Sheet
- **Preorder** (Root-L-R): serialize tree, copy tree
- **Inorder** (L-Root-R): BST → sorted order
- **Postorder** (L-R-Root): delete tree, calculate height
- **Level order** (BFS): level-by-level problems, min depth

## Complexity
- **Time:** O(n) — visit every node
- **Space:** O(h) DFS, O(w) BFS (h = height, w = max width)

## Edge Cases
- Null root
- Single node
- Skewed tree (becomes linked list)
- Disconnected graph (need visited set + loop over all nodes)

## Problems

| # | Problem | Difficulty | Key Trick |
|---|---|---|---|
| 1 | Level Order Traversal | Medium | BFS with size trick |
| 2 | Max Depth of Binary Tree | Easy | DFS, return 1 + max(left, right) |
| 3 | Validate BST | Medium | Inorder must be sorted / pass min-max range |
| 4 | Lowest Common Ancestor | Medium | Postorder: if left && right → root is LCA |
| 5 | Serialize/Deserialize Tree | Hard | Preorder + queue for deserialize |

## My Notes
<!-- Add your own observations, mistakes, and learnings below -->

