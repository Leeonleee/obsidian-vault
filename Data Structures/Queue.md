# Queue
An ADT that supports `enqueue` and `dequeue` operations

## Operations & Time Complexity

| Operation | Time Complexity | Notes                                                 |
| --------- | --------------- | ----------------------------------------------------- |
| enqueue   | $O(1)$          | adds element to queue                                 |
| dequeue   | $O(1)$          | removes first element of queue                        |
| first     | $O(1)$          | returns the element at the front of the queue         |
| size      | $O(1)$          | can be implemented using a counter in the queue class |
| is empty  | $O(1)$          |                                                       |
| search    | $O(n)$          | you need to dequeue until the value is found                                                      |

## Implementation
Can be implemented using [[Arrays]] or [[Linked Lists]]

### Advantages

### Disadvantages

## Edge cases
- Empty queue
- Queue with one element
- Queue with two elements

## Question Tips

## Techniques
