# Recursion Basics
Whiteboard walkthrough of a simple recursive solution for factorial using Matt Baker's stack visual method (see image below).

Highlight the idea of the base case and how that's usually the key for figuring out the recursive solution.

Iterative vs recursive. Iteration is a bird's eye view where you can see the whole problem. Recursion is tunnel vision on one part then punting the rest.

#### Iterative
```ruby
def factorial(n)
  sum = 1
  while n > 0
    sum *= n
    n -= 1
  end
  return sum
end
```

#### Recursive
```ruby
def factorial(n)
  return 1 if n <= 1
  n * factorial(n-1) 
end
```

![recursion stack](../../../../img/recursion.png)
