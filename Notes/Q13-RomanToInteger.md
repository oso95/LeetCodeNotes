# Q13: Roman to Integer

**LeveL: Easy**

-----

*Description*

Roman numerals are represented by seven different symbols: `I`, `V`, `X`, `L`, `C`, `D` and `M`.
`Symbol       Value
I             1
V             5
X             10
L             50
C             100
D             500
M             1000
`
For example, `2` is written as `II` in Roman numeral, just two one's added together. `12` is written as `XII`, which is simply `X + II`. The number `27` is written as `XXVII`, which is `XX + V + II`.

Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not `IIII`. Instead, the number four is written as `IV`. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as `IX`. There are six instances where subtraction is used:

* `I` can be placed before `V` (5) and `X` (10) to make 4 and 9.
* `X` can be placed before `L` (50) and `C` (100) to make 40 and 90.
* `C` can be placed before `D` (500) and `M` (1000) to make 400 and 900.

Given a roman numeral, convert it to an integer.

##### Example 1:
`Input: s = "III"
Output: 3`

##### Example 2:
`Input: s = "IV"
Output: 4`

##### Example 3:
`Input: s = "IX"
Output: 9`

##### Example 4:
`Input: s = "LVIII"
Output: 58
Explanation: L = 50, V= 5, III = 3.`

##### Example 5:
`Input: s = "MCMXCIV"
Output: 1994
Explanation: M = 1000, CM = 900, XC = 90 and IV = 4.`

##### Contraints:
`1 <= s.length <= 15
s contains only the characters ('I', 'V', 'X', 'L', 'C', 'D', 'M').
It is guaranteed that s is a valid roman numeral in the range [1, 3999].`


---------

# Solution 1

*Time: 44ms*

*Memory: 14.4MB*

*Test Cases Passed: 3999/3999*

```Python3
class Solution:
    def romanToInt(self, s: str) -> int:
        map = {'I': 1, 'IV': 4, 'V': 5, 'IX': 9, 'X': 10, 'XL': 40, 'L': 50, 'XC': 90, 'C': 100, 'CD':400, 'D': 500, 'CM':900,'M': 1000}
        num = 0
        i = 0
        while i < len(s):
            if i+1 < len(s) and s[i:i+2] in map:
                num = num + map[s[i:i+2]]
                i += 2
            else:
                num += map[s[i]]
                i+=1
        return num
```

**idea**

Creating a map for each roman numeral then using while loop to check thru each
elements in the string.

if `s[i:i+2]` (two numeral) is in the map we created then add value to num and
`i += 2` to skip the used roman numeral.


![image](https://github.com/cywang95/images/blob/main/LeetCode/Q13-RomanToInteger/1solution.png?raw=true)

![image](https://github.com/cywang95/images/blob/main/LeetCode/Q13-RomanToInteger/1solutionSubmission.png?raw=true)

---------

# Solution 2

*Time: 28ms*

*Memory: 14.3MB*

*Test Cases Passed: 3999/3999*

```Python3
class Solution:
    def romanToInt(self, s: str) -> int:
      res, prev = 0, 0
      dict = {'I':1, 'V':5, 'X':10, 'L':50, 'C':100, 'D':500, 'M':1000}

      for i in s[::-1]:          # rev the s
        if dict[i] >= prev:
          res += dict[i]     # sum the value iff previous value same or more

        else:
          res -= dict[i]     # substract when value is like "IV" --> 5-1, "IX" --> 10 -1 etc

        prev = dict[i]

      return res
```

**idea**

Faster solution found on the discussion place, it will reverse the roman numeral
and check if it is because then the previous one.


![image](https://github.com/cywang95/images/blob/main/LeetCode/Q13-RomanToInteger/2solution.png?raw=true)

![image](https://github.com/cywang95/images/blob/main/LeetCode/Q13-RomanToInteger/2solutionSubmission.png?raw=true)

-----

**Conclusion**

I was struggling one this question although I made a Roman numeral converter before.

Founding lack of ability is always good for me so I have idea how to improve myself.

----
*Date: 2021/7/14 12:01PM*

*Author: CYWang*
