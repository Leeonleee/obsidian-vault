# Stacks
An ADT that supports `push` and `pop` operations
- They are an important way of supporting nested/recursive function calls
- Used to implement depth-first search
## Operations & Time Complexity

| Operation | Time Complexity | Notes                                                 |
| --------- | --------------- | ----------------------------------------------------- |
| push      | $O(1)$          | adds element to stack                                 |
| pop       | $O(1)$          | removes and returns element at the top of the stack   |
| top/peek  | $O(1)$          | returns the element at the top of the stack           |
| size      | $O(1)$          | can be implemented using a counter in the stack class |
| is empty  | $O(1)$          |                                                       |
| search    | $O(n)$          |  you need to pop until the value is found                                                     |

## Implementation
Can be implemented using [[Arrays]] or [[Linked Lists]]

### Advantages
- Efficient because you only add/remove elements from the top of the stack

### Disadvantages
- Has limited functionality because it doesn't support many operations
- Is Last in, First Out (LIFO), which may not be ideal in all use cases

## Edge cases
- Empty stack
- Stack with one element
- Stack with two elements

## Question Tips

## Techniques
