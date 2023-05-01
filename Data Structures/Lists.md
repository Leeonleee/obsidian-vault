# Lists

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
Can be implemented using either [[Arrays]] or [[Linked Lists]]


### Advantages of [[Linked Lists|Linked List]] Implementation
- Efficient insertion and deletion
- Simpler behaviour as list grows
- Wastes no space as there is no maximum capacity

### Advantages of [[Arrays|Array]] Implementation
- No extra memory needed to store pointers
- Allows random access (retrieve element by index)

## Edge cases

## Question Tips

## Techniques
