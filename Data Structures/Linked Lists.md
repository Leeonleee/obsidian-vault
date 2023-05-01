# Linked Lists

## Types of Linked Lists

### Singly Linked List
- Each node points to the next node
### Doubly Linked List
- Each node points to the next and previous node
### Circular Linked List
- Each node points to the next node, but the last node points back to the first node
- In a circular doubly linked list, the first node's prev also points to the last node

## Operations & Time Complexity

| Operation    | Time Complexity | Notes                                                                                                                  |
| ------------ | --------------- | ---------------------------------------------------------------------------------------------------------------------- |
| access/get   | $O(n)$          | find element via index                                                                                                 |
| search       | $O(n)$          | traverse through linked list to find node                                                                                                                       | 
| insert first | $O(1)$          |                                                                                                                        |
| remove first | $O(1)$          |                                                                                                                        |
| insert       | $O(n)/O(1)$     | insert after given node. $O(n)$ in singly, $O(1)$ in doubly if we have a reference to the node we want to insert after |
| remove       | $O(n)/O(1)$     | $O(n)$ in singly. $O(1)$ in doubly if we have a reference to the node, else $O(n)$ as we need to find the node         |


## Implementation
Uses nodes that contain a pointer to the next node, and a pointer to the previous node if it's a doubly linked list

```python
class Node:
	def __init__(self, value):
		self.value = value
		self.next = None
		# optional
		self.prev = None

```

### Advantages
- Inserting and removing a node given it's location is $O(1)$ in a doubly linked list compared to $O(n)$ for an [[Arrays|Array]]

### Disadvantages
- Accessing/getting a value with an index is $O(n)$ because you need to start from the head
- Searching for a value is $O(n)$ because you need to start from the head

## Edge cases
- Empty linked list (head is `null`)
- Only one node
- Only two nodes
- Is it a circular linked list?
## Question Tips

## Techniques
