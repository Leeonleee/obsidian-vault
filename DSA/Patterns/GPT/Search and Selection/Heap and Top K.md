# Heap and Top K

Use a heap when you need repeated access to the smallest or largest item while processing data incrementally.

## Recognition Signals

- k largest / k smallest
- Running median or streaming updates
- Always need the next min or max
- Merge sorted lists

## Min-Heap Top K Largest

```python
import heapq

heap = []

for num in nums:
    heapq.heappush(heap, num)
    if len(heap) > k:
        heapq.heappop(heap)

return heap[0]
```

## Max-Heap Pattern in Python

```python
import heapq

heap = []
for num in nums:
    heapq.heappush(heap, -num)

largest = -heapq.heappop(heap)
```

## Merge k Sorted Lists Idea

- Push the first item from each list into a heap
- Pop the smallest
- Push the next item from the same list

## Pitfalls

- Using a full sort when streaming is better
- Forgetting Python `heapq` is a min-heap
- Not storing tie-break fields for tuple comparisons when needed

## Related Problems

- Kth Largest Element in a Stream
- Top K Frequent Elements
- Merge k Sorted Lists
- Find Median from Data Stream
