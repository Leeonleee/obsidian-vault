# LeetCode Reference

Central index for common DSA patterns, recognition cues, and reusable Python snippets.

## How to Use This

1. Start here when a problem feels familiar but you cannot name the pattern yet.
2. Jump into the category that best matches the problem shape.
3. Open a pattern note and scan:
   - recognition signals
   - core idea
   - template
   - pitfalls
   - related problems
4. When you learn a new pattern, duplicate [[Templates/Pattern Template]] and place it in the right category folder.

## Folder Structure

- `Patterns/Array and String`
- `Patterns/Search and Selection`
- `Patterns/Graphs and Trees`
- `Patterns/Recursion and DP`
- `Templates`

## Pattern Index

### Array and String

- [[DSA/Patterns/GPT/Array and String/Index|Array and String Index]]
- [[Two Pointers]]
- [[Sliding Window]]
- [[Fast and Slow Pointers]]
- [[Prefix Sum and Hash Map]]

### Search and Selection

- [[DSA/Patterns/GPT/Search and Selection/Index|Search and Selection Index]]
- [[Binary Search]]
- [[Heap and Top K]]

### Graphs and Trees

- [[DSA/Patterns/GPT/Graphs and Trees/Index|Graphs and Trees Index]]
- [[Trees and Graph Traversal]]
- [[2 Colouring]]

### Recursion and DP

- [[DSA/Patterns/GPT/Recursion and DP/Index|Recursion and DP Index]]
- [[Backtracking]]
- [[Dynamic Programming]]

## Quick Recognition Guide

| If you see... | Likely pattern |
| --- | --- |
| Sorted array, pair/triplet, shrink from ends | [[Two Pointers]] |
| Contiguous subarray/substring | [[Sliding Window]] |
| Sorted search space, answer is monotonic | [[Binary Search]] |
| Cycle in linked list, midpoint, repeated state | [[Fast and Slow Pointers]] |
| Tree levels, connected components, shortest path in unweighted graph | [[Trees and Graph Traversal]] |
| Generate all combinations/permutations/subsets | [[Backtracking]] |
| "Best/ways/min steps/max score" with overlapping subproblems | [[Dynamic Programming]] |
| Repeated top/min/max extraction, k largest/smallest, streaming | [[Heap and Top K]] |
| Subarray sum/count, running totals, frequency lookups | [[Prefix Sum and Hash Map]] |
| Two groups, enemy relationships, odd cycle detection | [[2 Colouring]] |

## Interview Checklist

- Clarify input size before choosing brute force vs optimized.
- Ask whether the input is sorted, mutable, unique, or may contain negatives.
- Write down the invariant before coding.
- Validate edge cases early: empty input, one element, duplicates, overflow boundaries.
- Trace the template on a tiny example before finalizing.

## Add a New Pattern

1. Duplicate [[Templates/Pattern Template]].
2. Place it in the most appropriate category folder under `Patterns/`.
3. Add the new note to the matching section in this index.
4. Add a row to the recognition guide if it has a clear trigger phrase.
