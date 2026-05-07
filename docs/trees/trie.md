# Trie

## When to Use
- Prefix matching / autocomplete
- Word search in dictionary
- Clue words: "prefix", "dictionary", "word search", "autocomplete"

## Template

### Trie Implementation
```java
class TrieNode {
    TrieNode[] children = new TrieNode[26];
    boolean isEnd = false;
}

class Trie {
    TrieNode root = new TrieNode();

    void insert(String word) {
        TrieNode node = root;
        for (char c : word.toCharArray()) {
            int idx = c - 'a';
            if (node.children[idx] == null) node.children[idx] = new TrieNode();
            node = node.children[idx];
        }
        node.isEnd = true;
    }

    boolean search(String word) {
        TrieNode node = find(word);
        return node != null && node.isEnd;
    }

    boolean startsWith(String prefix) {
        return find(prefix) != null;
    }

    private TrieNode find(String s) {
        TrieNode node = root;
        for (char c : s.toCharArray()) {
            int idx = c - 'a';
            if (node.children[idx] == null) return null;
            node = node.children[idx];
        }
        return node;
    }
}
```

### Word Search II (Trie + Backtracking)
```java
void dfs(char[][] board, int r, int c, TrieNode node, StringBuilder sb, List<String> result) {
    if (r < 0 || r >= board.length || c < 0 || c >= board[0].length || board[r][c] == '#') return;
    char ch = board[r][c];
    TrieNode next = node.children[ch - 'a'];
    if (next == null) return;
    sb.append(ch);
    if (next.isEnd) { result.add(sb.toString()); next.isEnd = false; }
    board[r][c] = '#';
    int[][] dirs = {{0,1},{0,-1},{1,0},{-1,0}};
    for (int[] d : dirs) dfs(board, r + d[0], c + d[1], next, sb, result);
    board[r][c] = ch;
    sb.deleteCharAt(sb.length() - 1);
}
```

## Key Problems
| Problem | Approach |
|---------|----------|
| Implement Trie | Array of 26 children per node |
| Word Search II | Trie + grid backtracking |
| Design Search Autocomplete | Trie + frequency tracking |
| Replace Words | Insert roots, match prefixes |
| Longest Word in Dictionary | Trie + BFS/DFS |
