# Q9: Palindrome number

**LeveL: Easy**

-----

*Description*

Given an integer `x`, return true if `x` is palindrome integer.

An integer is a **palindrome** when it reads the same backward as forward.

For example, `121` is palindrome while `123` is not.


##### Example 1:
`Input: x = 121
Output: true`

##### Example 2:
`Input: x = -121
Output: false
Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.`

##### Example 3:
`Input: x = 10
Output: false
Explanation: Reads 01 from right to left. Therefore it is not a palindrome.`

##### Example 4:
`Input: x = -101
Output: false`

##### Contraints:
`-2^31 <= x <= 2^31 - 1`

##### Follow up:
`Could you solve it without converting the integer to a string?`

---------

# Solution 1

*Time: 80ms*

*Memory: 14.4MB*

*Test Cases Passed: 11510/11510*


```Python3

class Solution:
    def isPalindrome(self, x: int) -> bool:
        if x >= 0:
            rev = 0
            temp = x      
            while(temp != 0):
                rev = rev*10 + temp%10
                temp//=10
            return True if x == rev else False

        else:
            return False

```

**idea**

If `x` is negative then it will never be palindrome number so we can just return
`False` if it's negative.

When `x` is positive, we simply reverse it's number in a while loop until we
reversed all the numbers.

Then we return the result by using if-else, (I learned this from Q7 solution,
  check it out if you interest. [Q7-ReverseInteger](https://github.com/cywang95/LeetCodeNotes/blob/main/Notes/Q7-ReverseInteger.md))


![image](https://github.com/cywang95/images/blob/main/LeetCode/Q9-Palindrome%20Number/NoStrResult.png?raw=true)

![image](https://github.com/cywang95/images/blob/main/LeetCode/Q9-Palindrome%20Number/NoStr3Submission.png?raw=true)


------

# Solution 2

*Time: 44ms*

*Memory: 14.3MB*

*Test Cases Passed: 11510/11510*


```Python3

class Solution:
    def isPalindrome(self, x: int) -> bool:
        if x >= 0:
            return True if int(str(x)[::-1]) == x else False     
        else:
            return False

```


**Idea**


Although the question ask us not to use `str()` but I also want to bring this
out to show the different between it.

The time complexity is playing a crucial role in this problem as we saw in the
Q7-ReverseInteger.


![image](https://github.com/cywang95/images/blob/main/LeetCode/Q9-Palindrome%20Number/Result.png?raw=true)

![image](https://github.com/cywang95/images/blob/main/LeetCode/Q9-Palindrome%20Number/3submission.png?raw=true)



-----

**Conclusion**

It took me about 3 mins to solve this question with both methods, but the most
impressive part is that I noticed how similar this question is compare it to the
Q7.

I found that writing down the note actually helps me to understand and remind me
faster when I see problem.

I will keep this up and keep improve myself.

----
*Date: 2021/7/11 8:31PM*

*Author: CYWang*
