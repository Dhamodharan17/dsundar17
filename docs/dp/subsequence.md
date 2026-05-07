# Subsequence Pattern (DP)

## When to Use
- Compare two strings/arrays
- Longest common subsequence / substring
- Edit distance
- Clue words: "subsequence", "common", "edit distance", "interleaving"

## Variants

| Pattern | DP Meaning |
|---|---|
| LCS | dp[i][j] = LCS of s1[0..i-1] and s2[0..j-1] |
| LIS | dp[i] = length of LIS ending at index i |
| Edit Distance | dp[i][j] = min ops to convert s1[0..i-1] → s2[0..j-1] |

## Template

### Longest Common Subsequence (LCS)
```java
int lcs(String s1, String s2) {
    int m = s1.length(), n = s2.length();
    int[][] dp = new int[m + 1][n + 1];

    for (int i = 1; i <= m; i++) {
        for (int j = 1; j <= n; j++) {
            if (s1.charAt(i - 1) == s2.charAt(j - 1)) {
                dp[i][j] = dp[i - 1][j - 1] + 1;
            } else {
                dp[i][j] = Math.max(dp[i - 1][j], dp[i][j - 1]);
            }
        }
    }
    return dp[m][n];
}
```

### Longest Increasing Subsequence (LIS) — O(n log n)
```java
int lis(int[] nums) {
    List<Integer> tails = new ArrayList<>();
    for (int num : nums) {
        int pos = Collections.binarySearch(tails, num);
        if (pos < 0) pos = -(pos + 1);
        if (pos == tails.size()) tails.add(num);
        else tails.set(pos, num);
    }
    return tails.size();
}
```

### Edit Distance
```java
int editDistance(String s1, String s2) {
    int m = s1.length(), n = s2.length();
    int[][] dp = new int[m + 1][n + 1];

    for (int i = 0; i <= m; i++) dp[i][0] = i; // delete all
    for (int j = 0; j <= n; j++) dp[0][j] = j; // insert all

    for (int i = 1; i <= m; i++) {
        for (int j = 1; j <= n; j++) {
            if (s1.charAt(i - 1) == s2.charAt(j - 1)) {
                dp[i][j] = dp[i - 1][j - 1];
            } else {
                dp[i][j] = 1 + Math.min(dp[i - 1][j - 1],  // replace
                            Math.min(dp[i - 1][j],            // delete
                                     dp[i][j - 1]));          // insert
            }
        }
    }
    return dp[m][n];
}
```

## Complexity
- **LCS / Edit Distance:** O(m × n) time, O(m × n) space (O(n) with rolling array)
- **LIS:** O(n log n) with binary search, O(n²) brute force

## Edge Cases
- Empty strings
- Identical strings
- One string is subsequence of other
- Single character strings

## Problems

| # | Problem | Difficulty | Key Trick |
|---|---|---|---|
| 1 | Longest Common Subsequence | Medium | 2D DP, match → diagonal + 1 |
| 2 | Longest Increasing Subsequence | Medium | Binary search on tails |
| 3 | Edit Distance | Medium | 3 operations = min of 3 cells |
| 4 | Longest Palindromic Subsequence | Medium | LCS(s, reverse(s)) |
| 5 | Shortest Common Supersequence | Hard | LCS + reconstruct |

## My Notes
<!-- Add your own observations, mistakes, and learnings below -->

