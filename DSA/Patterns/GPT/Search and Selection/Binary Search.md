# Binary Search

Use binary search when the search space is ordered or the answer changes monotonically from false to true.

## Recognition Signals

- Sorted array
- Need first/last position
- "Minimum feasible" or "maximum possible" answer
- Can write a monotonic `can_do(mid)` check

## Exact Match

```python
left, right = 0, len(nums) - 1

while left <= right:
    mid = (left + right) // 2

    if nums[mid] == target:
        return mid
    if nums[mid] < target:
        left = mid + 1
    else:
        right = mid - 1

return -1
```

## First True Pattern

```python
left, right = low, high

while left < right:
    mid = (left + right) // 2
    if can_do(mid):
        right = mid
    else:
        left = mid + 1

return left
```

## Questions to Ask

- What are the low/high bounds?
- Does `mid` belong to the left half or right half on success?
- Am I searching values, indices, or answer space?

## Pitfalls

- Off-by-one errors from mixing `left < right` and `left <= right`
- Overflow in other languages when computing `mid`
- Using binary search when the predicate is not monotonic

## Related Problems

- Binary Search
- Search Insert Position
- First Bad Version
- Koko Eating Bananas
- Search in Rotated Sorted Array
