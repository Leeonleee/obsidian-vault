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

| Operation | Time Complexity | Notes |
| ----------|-----------------|-------| 
| access/get | $O(n)$ |find element via index|
| search | $O(n)$ ||
|insert first| $O(1)$||
| remove first | $O(1)$ ||
| insert | $O(n)/O(1)$ |insert after given node. $O(n)$ in singly, $O(1)$ in doubly if we have a reference to the node we want to insert after|
| remove | $O(n)/O(1)$|$O(n)$ in singly. $O(1)$ in doubly if we have a reference to the node, else $O(n)$ as we need to find the node |


## Implementation



### Advantages

### Disadvantages

## Edge cases

## Question Tips

## Techniques
