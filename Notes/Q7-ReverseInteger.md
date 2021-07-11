# Q7: Reverse Integer

**LeveL: Easy**

-----

*Description*

Given a signed 32-bit integer `x`, return `x` with its digits reversed. If reversing `x` causes the value to go outside the signed 32-bit integer range `[-2^31, 2^31 - 1]`, then return `0`.

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

*Time: 52ms*

*Memory: 14.3MB*

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

First we need to check if the input number is in the range of `-2^31 <= x <= 2^31 - 1`.
Then we use a `while loop` to reverse number step by step until nothing left.
If the input is negative, we convert it into positive first then do the same process
until we get the answer we want.


![image](https://github.com/cywang95/images/blob/main/LeetCode/Q7-ReverseInt/1stSubmission.png?raw=true)


result in 3 submissions
![image](https://github.com/cywang95/images/blob/main/LeetCode/Q7-ReverseInt/1stTotalSubmissions.png?raw=true)



------

# Solution 2

*Time: 36ms*

*Memory: 14.3MB*

*Test Cases Passed: 1032/1032*


```Python3

class Solution:
    def reverse(self, x: int) -> int:
        rev = int(str(abs(x))[::-1])
        return (-rev if x < 0 else rev) if rev.bit_length() < 32 else 0


```


**idea**

I found this most voted solution in discussion. The idea is use `abs(x)` to turn
`x` into absolute value and then convert it into string in reverse way by using
`[::-1]`.

*[::-1] will read the elements from back to beginning*

Then use `.big_length()` to check if its smaller than 32 bits.

![image](https://github.com/cywang95/images/blob/main/LeetCode/Q7-ReverseInt/2LineSubmission.png?raw=true)


result in 3 submissions
![image](https://github.com/cywang95/images/blob/main/LeetCode/Q7-ReverseInt/2ndTotalSubmissions.png?raw=true)


-----
*Date: 2021/7/11 8:31PM*

*Author: CYWang*
