# Arrays

## Operations & Time Complexity
| Operation | Time Complexity | Notes |
| ----------|-----------------|-------| 
| access/get | $O(1)$ | |
| Search | $O(n)$| |
| Search | $O(log (n))$ | |
| insert/add | $O(n)$ | Shifts all elements after $n$ to the right by one|
| insert/add (end of array) | $O(1)$) | No elements need to be shifted|
| remove | $O(n)$ | Shifts all elements after $n$ to the left by one|
|remove (end of array) | $O(1)$ | No elements need to be shifted |
| size | $O(1)$ | number of elements in array|
| is empty | $O(1)$ | |

## Implementation
Built in to most languages

### Advantages
- Can store multiple elements of the same time with just one variable
- Accessing elements is fast if you have the index
### Disadvantages
- Adding and removing from the middle of the array is slow because you need to shift elements
- Arrays have fixed sizes in certain languages

## Edge cases
- Empty Arrays
- Duplicate values

## Question Tips

## Techniques
Strings are just arrays of characters, so most techniques for arrays will apply for strings
