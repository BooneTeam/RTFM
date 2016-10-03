# Binary Search

Whiteboard walkthrough of recursive solution of binary search

#### Base Cases
1) Reached the end of the array (cut it down to length 1)
2) found the item searched for

#### Code
```ruby
# assume a sorted array
def binary_search(query, array)
  if array.length == 1
    return false if query == array[0]
    # return query == array[0] (better alternative for above line)
  index = array.length/2
  if query == array[index]
    return true
  elsif query > array[index]
    binary_search(query, array.slice(index, array.length))
  elsif query < array[index]
    binary_search(query, array.slice(0, index))
end
```
