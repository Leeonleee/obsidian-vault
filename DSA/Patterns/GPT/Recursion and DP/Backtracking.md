# Backtracking

Backtracking builds candidates incrementally, explores a choice, then undoes it before the next branch.

## Recognition Signals

- Generate all combinations, permutations, or subsets
- Need every valid arrangement
- Constraints can prune branches early

## Subsets Template

```python
result = []
path = []

def backtrack(start):
    result.append(path[:])

    for i in range(start, len(nums)):
        path.append(nums[i])
        backtrack(i + 1)
        path.pop()

backtrack(0)
return result
```

## Permutations Template

```python
result = []
path = []
used = [False] * len(nums)

def backtrack():
    if len(path) == len(nums):
        result.append(path[:])
        return

    for i in range(len(nums)):
        if used[i]:
            continue
        used[i] = True
        path.append(nums[i])
        backtrack()
        path.pop()
        used[i] = False

backtrack()
return result
```

## Pruning Ideas

- Stop when partial state is already invalid
- Skip duplicates after sorting
- Track remaining capacity, remaining sum, or remaining choices

## Pitfalls

- Forgetting to undo state on the way back up
- Mutating and appending the same list reference
- Missing duplicate-skipping logic

## Related Problems

- Subsets
- Permutations
- Combination Sum
- Palindrome Partitioning
- N-Queens
