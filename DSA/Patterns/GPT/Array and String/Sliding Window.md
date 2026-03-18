# Sliding Window

Use a moving window over a contiguous range when the problem asks about subarrays or substrings.

## Recognition Signals

- "Longest", "shortest", "count", or "max" over contiguous elements
- Substring/subarray constraints
- Need to expand and shrink efficiently

## Fixed-Size Window

```python
window_sum = sum(nums[:k])
best = window_sum

for right in range(k, len(nums)):
    window_sum += nums[right]
    window_sum -= nums[right - k]
    best = max(best, window_sum)

return best
```

## Variable-Size Window

```python
left = 0
window = {}
best = 0

for right, ch in enumerate(s):
    window[ch] = window.get(ch, 0) + 1

    while not valid(window):
        left_ch = s[left]
        window[left_ch] -= 1
        if window[left_ch] == 0:
            del window[left_ch]
        left += 1

    best = max(best, right - left + 1)

return best
```

## Core Invariant

Maintain a window that is either:

- always valid, then update answer after shrinking
- allowed to become invalid temporarily, then shrink until valid again

## Pitfalls

- Updating the answer at the wrong time
- Using sliding window when negatives break the monotonic property
- Forgetting to remove zero-count entries from maps

## Related Problems

- Longest Substring Without Repeating Characters
- Minimum Window Substring
- Permutation in String
- Maximum Average Subarray I
