# Lists

## Operations & Time Complexity

### Array Implementation

| Operation | Time Complexity | Notes              |
| --------- | --------------- | ------------------ |
| size      | $O(1)           | number of elements | 
|           |                 |                    |

### Linked List Implementation
| Operation    | Time Complexity | Notes                                                                                                                  |
| ------------ | --------------- | ---------------------------------------------------------------------------------------------------------------------- |
| search       | $O(n)$          | traverse through each element to find node                                                                             |
| insert first | $O(1)$          |                                                                                                                        |
| remove first | $O(1)$          |                                                                                                                        |
| insert       | $O(n)/O(1)$     | insert after given node. $O(n)$ in singly, $O(1)$ in doubly if we have a reference to the node we want to insert after |
| remove       | $O(n)/O(1)$     | $O(n)$ in singly. $O(1)$ in doubly if we have a reference to the node, else $O(n)$ as we need to find the node         |
| size         | $O(n)$          | traverse through linked list with a counter                                                                            |
| first        | $O(1)$          |                                                                                                                        |
| is empty     | $O(1)$          | checks if head is `null`                                                                                                                       |




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
