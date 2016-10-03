# Recursion Basics Breakout
Whiteboard walkthrough of a simple recursive solution for factorial using Matt Baker's stack visual method (see image below)

```ruby
def factorial(n, total)
  if n<=1
    return total
  end
  factorial(n-1, n*total)
end
```


![recursion stack](../../img/recursion.png)
