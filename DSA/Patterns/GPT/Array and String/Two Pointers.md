# Two Pointers

Use two indices that move through the input together, usually from opposite ends or with a slow/fast layout.

## Recognition Signals

- Array or string problem
- Sorted input
- Need a pair/triplet
- Need in-place compaction or partitioning

## Common Variants

- Opposite ends: `left`, `right`
- Same direction: slow/fast pointer
- Fixed one index + move two pointers for `3Sum` style problems

## Template

```python
left, right = 0, len(nums) - 1

while left < right:
    curr = nums[left] + nums[right]

    if curr == target:
        return [left, right]
    if curr < target:
        left += 1
    else:
        right -= 1

return None
```

## In-Place Write Template

```python
write = 0

for read in range(len(nums)):
    if keep(nums[read]):
        nums[write] = nums[read]
        write += 1

return write
```

## Pitfalls

- Forgetting the sorted precondition
- Infinite loops from missing pointer movement
- Mishandling duplicates in `3Sum` / `4Sum`

## Related Problems

- Two Sum II
- Container With Most Water
- Valid Palindrome
- 3Sum
- Remove Duplicates from Sorted Array
