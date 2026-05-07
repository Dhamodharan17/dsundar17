# Graph

## When to Use
- Connected components, shortest paths
- Cycle detection, topological sort
- Network flow, island problems
- Clue words: "connected", "path", "network", "grid", "island"

## Representations
```java
// Adjacency List
List<List<Integer>> graph = new ArrayList<>();
for (int i = 0; i < n; i++) graph.add(new ArrayList<>());
graph.get(u).add(v);

// Adjacency Matrix
int[][] graph = new int[n][n];
graph[u][v] = 1;
```

## Templates

### BFS (Shortest Path in Unweighted Graph)
```java
Queue<Integer> queue = new LinkedList<>();
boolean[] visited = new boolean[n];
queue.offer(start);
visited[start] = true;
int level = 0;
while (!queue.isEmpty()) {
    int size = queue.size();
    for (int i = 0; i < size; i++) {
        int node = queue.poll();
        for (int neighbor : graph.get(node)) {
            if (!visited[neighbor]) {
                visited[neighbor] = true;
                queue.offer(neighbor);
            }
        }
    }
    level++;
}
```

### DFS (Cycle Detection - Directed)
```java
// 0 = unvisited, 1 = in-progress, 2 = done
int[] state = new int[n];
boolean hasCycle(int node) {
    if (state[node] == 1) return true;  // back edge
    if (state[node] == 2) return false;
    state[node] = 1;
    for (int neighbor : graph.get(node)) {
        if (hasCycle(neighbor)) return true;
    }
    state[node] = 2;
    return false;
}
```

### Topological Sort (Kahn's BFS)
```java
int[] inDegree = new int[n];
for (int u = 0; u < n; u++)
    for (int v : graph.get(u)) inDegree[v]++;

Queue<Integer> queue = new LinkedList<>();
for (int i = 0; i < n; i++)
    if (inDegree[i] == 0) queue.offer(i);

List<Integer> order = new ArrayList<>();
while (!queue.isEmpty()) {
    int node = queue.poll();
    order.add(node);
    for (int neighbor : graph.get(node)) {
        if (--inDegree[neighbor] == 0) queue.offer(neighbor);
    }
}
```

### Dijkstra (Shortest Path - Weighted)
```java
int[] dist = new int[n];
Arrays.fill(dist, Integer.MAX_VALUE);
dist[start] = 0;
PriorityQueue<int[]> pq = new PriorityQueue<>((a, b) -> a[1] - b[1]);
pq.offer(new int[]{start, 0});
while (!pq.isEmpty()) {
    int[] curr = pq.poll();
    int u = curr[0], d = curr[1];
    if (d > dist[u]) continue;
    for (int[] edge : graph.get(u)) { // {neighbor, weight}
        int v = edge[0], w = edge[1];
        if (dist[u] + w < dist[v]) {
            dist[v] = dist[u] + w;
            pq.offer(new int[]{v, dist[v]});
        }
    }
}
```

### Union-Find
```java
int[] parent, rank;
int find(int x) {
    if (parent[x] != x) parent[x] = find(parent[x]);
    return parent[x];
}
void union(int x, int y) {
    int px = find(x), py = find(y);
    if (px == py) return;
    if (rank[px] < rank[py]) parent[px] = py;
    else if (rank[px] > rank[py]) parent[py] = px;
    else { parent[py] = px; rank[px]++; }
}
```

## Key Problems
| Problem | Approach |
|---------|----------|
| Number of Islands | BFS/DFS on grid |
| Course Schedule | Topological sort / cycle detection |
| Clone Graph | BFS/DFS + HashMap |
| Network Delay Time | Dijkstra |
| Accounts Merge | Union-Find |
Graph - 227
AVl - 297