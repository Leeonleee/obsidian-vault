# Dynamic Programming

Use DP when subproblems overlap and the answer can be built from smaller states.

## Recognition Signals

- "How many ways"
- "Minimum" or "maximum" over choices
- Repeated recursive structure
- Decision at index `i` depends on previous results

## Workflow

1. Define the state clearly.
2. Write the recurrence.
3. Choose top-down memoization or bottom-up tabulation.
4. Set base cases.
5. Check iteration order.

## 1D DP Template

```python
dp = [0] * (n + 1)
dp[0] = base

for i in range(1, n + 1):
    dp[i] = transition(dp, i)

return dp[n]
```

## Memoization Template

```python
from functools import cache

@cache
def dfs(i):
    if i == base_case:
        return base_value

    ans = 0
    for choice in choices(i):
        ans = best(ans, dfs(next_state(i, choice)))
    return ans
```

## Common State Shapes

- Index only: `dp[i]`
- Index + extra state: `dp[i][j]`
- Grid cell: `dp[r][c]`
- Decision on prefix/suffix

## Pitfalls

- State is too vague or too large
- Wrong iteration order
- Forgetting base cases and impossible states

## Related Problems

- Climbing Stairs
- House Robber
- Coin Change
- Longest Increasing Subsequence
- Edit Distance
