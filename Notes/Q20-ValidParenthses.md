# Q20: Valid Parentheses

**Level: Easy**

----

**Solution**

```Python3

d = { '(': ')', '[': ']', '{': '}'}
stack = []


for i in s:
  if i in d:
    stack.append(i)
  elif len(stack) == 0 or d[stack.pop()] != i:
    return False

return len(stack) == 0

```

**idea**

The last open parentheses need to close first. Using dictionary of python could helping to pair the parentheses.

using stack (list) could reduce the time complexity.

----

*Date: 2022/6/14*
*Author: CYWang*
