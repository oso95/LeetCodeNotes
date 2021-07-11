# Q7: Reverse Integer

**LeveL: Easy**

-----

*Description*

Given a signed 32-bit integer `x`, return `x` with its digits reversed. If reversing `x` causes the value to go outside the signed 32-bit integer range `[$-2^31$, $2^31$ - 1]`, then return `0`.

**Assume the environment does not allow you to store 64-bit integers (signed or unsigned).**

##### Example 1:
`Input: x = 123
Output: 321`

##### Example 2:
`Input: x = -123
Output: -321`

##### Example 3:
`Input: x = 120
Output: 21`

##### Example 4:
`Input: x = 0
Output: 0`

##### Contraints:
`-2^31 <= x <= 2^31 - 1`


---------

# Solution 1

*Time: 72ms*

*Memory: 14.2MB*

*Test Cases Passed: 1032/1032*

```Python3

class Solution:
    def reverse(self, x: int) -> int:
        oneDigit = 0
        reNum = 0
        isNegative = False

        if 2147483647 >= x >= -2147483647:
            while x != 0:
                if x >= 1:
                    oneDigit = x % 10
                    reNum = reNum * 10 + oneDigit
                    x = x - oneDigit
                    x//=10

                if x <= -1:

                    x = -x
                    oneDigit = x % 10
                    reNum = reNum * 10 + oneDigit
                    x = x - oneDigit
                    x /= 10
                    isNegative = True

            if (isNegative) and (2147483647 >= reNum >= -2147483647):
                reNum = -reNum
                return(int(reNum))
            elif (2147483647 >= reNum >= -2147483647):
                return(int(reNum))
            else:
                return 0
        else:
            return 0

```


**Idea**

First we need to check if the input number is in the range of `$-2^31$ <= x <= $2^31$ - 1`.
