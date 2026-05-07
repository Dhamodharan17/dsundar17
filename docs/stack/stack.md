# Stack

## When to Use
- Matching brackets, parentheses
- Monotonic stack (next greater/smaller element)
- Expression evaluation
- Clue words: "next greater", "valid parentheses", "evaluate", "histogram"

## Templates

### Monotonic Stack (Next Greater Element)
```java
int[] result = new int[nums.length];
Arrays.fill(result, -1);
Deque<Integer> stack = new ArrayDeque<>(); // stores indices
for (int i = 0; i < nums.length; i++) {
    while (!stack.isEmpty() && nums[stack.peek()] < nums[i]) {
        result[stack.pop()] = nums[i];
    }
    stack.push(i);
}
```

### Valid Parentheses
```java
Deque<Character> stack = new ArrayDeque<>();
for (char c : s.toCharArray()) {
    if (c == '(') stack.push(')');
    else if (c == '{') stack.push('}');
    else if (c == '[') stack.push(']');
    else if (stack.isEmpty() || stack.pop() != c) return false;
}
return stack.isEmpty();
```

### Min Stack
```java
Deque<int[]> stack = new ArrayDeque<>(); // {val, currentMin}
void push(int val) {
    int min = stack.isEmpty() ? val : Math.min(val, stack.peek()[1]);
    stack.push(new int[]{val, min});
}
int getMin() { return stack.peek()[1]; }
```

## Key Problems
| Problem | Approach |
|---------|----------|
| Next Greater Element | Monotonic stack |
| Largest Rectangle in Histogram | Monotonic stack of indices |
| Valid Parentheses | Push expected closing bracket |
| Daily Temperatures | Monotonic stack |
| Evaluate Reverse Polish Notation | Stack of operands |
