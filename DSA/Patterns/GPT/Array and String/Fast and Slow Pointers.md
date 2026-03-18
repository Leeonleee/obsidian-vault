# Fast and Slow Pointers

Use different pointer speeds to detect cycles or find relative positions in linked structures.

## Recognition Signals

- Linked list cycle detection
- Find middle node
- Find kth node from the end
- Repeated state that loops

## Cycle Detection

```python
slow = fast = head

while fast and fast.next:
    slow = slow.next
    fast = fast.next.next
    if slow == fast:
        return True

return False
```

## Middle of Linked List

```python
slow = fast = head

while fast and fast.next:
    slow = slow.next
    fast = fast.next.next

return slow
```

## Remove Nth From End

```python
dummy = ListNode(0, head)
slow = fast = dummy

for _ in range(n + 1):
    fast = fast.next

while fast:
    slow = slow.next
    fast = fast.next

slow.next = slow.next.next
return dummy.next
```

## Pitfalls

- Forgetting a dummy node for head deletion cases
- Not checking `fast` and `fast.next`
- Confusing "middle" behavior for even-length lists

## Related Problems

- Linked List Cycle
- Middle of the Linked List
- Remove Nth Node From End of List
- Happy Number
