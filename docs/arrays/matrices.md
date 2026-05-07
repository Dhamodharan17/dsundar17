# Matrices

## When to Use
- 2D grid traversal
- Matrix rotation / transformation
- Search in sorted matrix
- Clue words: "grid", "matrix", "rotate", "spiral", "island"

## Templates

### Grid DFS (Island counting)
```java
int[][] dirs = {{0,1},{0,-1},{1,0},{-1,0}};
void dfs(int[][] grid, int r, int c) {
    if (r < 0 || r >= grid.length || c < 0 || c >= grid[0].length || grid[r][c] == 0) return;
    grid[r][c] = 0; // mark visited
    for (int[] d : dirs) dfs(grid, r + d[0], c + d[1]);
}
```

### Spiral Order
```java
List<Integer> result = new ArrayList<>();
int top = 0, bottom = m - 1, left = 0, right = n - 1;
while (top <= bottom && left <= right) {
    for (int j = left; j <= right; j++) result.add(matrix[top][j]);
    top++;
    for (int i = top; i <= bottom; i++) result.add(matrix[i][right]);
    right--;
    if (top <= bottom) {
        for (int j = right; j >= left; j--) result.add(matrix[bottom][j]);
        bottom--;
    }
    if (left <= right) {
        for (int i = bottom; i >= top; i--) result.add(matrix[i][left]);
        left++;
    }
}
```

### Rotate Matrix 90° Clockwise
```java
// Transpose + reverse each row
int n = matrix.length;
for (int i = 0; i < n; i++)
    for (int j = i; j < n; j++) {
        int temp = matrix[i][j];
        matrix[i][j] = matrix[j][i];
        matrix[j][i] = temp;
    }
for (int[] row : matrix) {
    int l = 0, r = n - 1;
    while (l < r) { int tmp = row[l]; row[l++] = row[r]; row[r--] = tmp; }
}
```

### Search Sorted Matrix
```java
// Start from top-right corner
int r = 0, c = matrix[0].length - 1;
while (r < matrix.length && c >= 0) {
    if (matrix[r][c] == target) return true;
    else if (matrix[r][c] > target) c--;
    else r++;
}
return false;
```

## Key Problems
| Problem | Approach |
|---------|----------|
| Number of Islands | DFS/BFS on grid |
| Spiral Matrix | Layer by layer traversal |
| Rotate Image | Transpose + reverse |
| Set Matrix Zeroes | Use first row/col as markers |
| Search a 2D Matrix II | Start top-right corner |
