# Prefix Sum and Hash Map

Use prefix sums to turn repeated range calculations into constant-time lookups. Combine with a hash map when counting or detecting prior states.

## Recognition Signals

- Subarray sum equals `k`
- Count of ranges satisfying a condition
- Need fast repeated sum queries
- Running total + previous occurrence matters

## Prefix Sum Template

```python
prefix = [0]

for num in nums:
    prefix.append(prefix[-1] + num)

range_sum = prefix[right + 1] - prefix[left]
```

## Subarray Sum Equals k

```python
count = 0
curr = 0
seen = {0: 1}

for num in nums:
    curr += num
    count += seen.get(curr - k, 0)
    seen[curr] = seen.get(curr, 0) + 1

return count
```

## Key Idea

If `prefix[j] - prefix[i] = k`, then `prefix[i] = prefix[j] - k`.

## Pitfalls

- Sliding window does not replace this when negatives exist
- Forgetting the initial `0: 1` seed in counting problems
- Mixing up count vs earliest index in the hash map

## Related Problems

- Range Sum Query
- Subarray Sum Equals K
- Continuous Subarray Sum
- Contiguous Array
