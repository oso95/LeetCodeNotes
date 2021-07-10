# Two Sums

------

*Description*

Given an array of integers `nums` and an integer `target`, return indices of the two numbers such that they add up to `target`.

You may assume that each input would have **exactly one solution**, and you may **not** use the same element twice.

You can return the answer in any order.



*In/Output example*
![image](https://github.com/cywang95/images/blob/main/LeetCode/Q1-TwoSum/InOutPutExamle.png?raw=true)

*Additional Information*

![image](https://github.com/cywang95/images/blob/main/LeetCode/Q1-TwoSum/otherRequirement.png?raw=true)

-----

# Solution 1

**First Attend**

*Time: Time Limit Exceeded*

*Memory: -*

*Test Cases Passed: 53/54*



*Python3 Code*

```Python3

class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for i in range(len(nums)):
            for j in range(len(nums)):
                if (i != j):
                    if(nums[i] + nums[j]) == target:
                        return i,j

```




*idea:*
Using two loop to read thru all the numbers from the array.

Since we can not use same element twice, I added condition `if i != j` to make
sure they are different elements.

Follow by that, if they are different element and the sums of it is equal to the
given `target`, then we return `i` and `j`.

On my first submission, it returns an error of **Time Limit Exceeded** because
using two loops to read all the values taking too much time.

![image](https://github.com/cywang95/images/blob/main/LeetCode/Q1-TwoSum/SolutionError.png?raw=true)

Before I tried other solution, I decided to submit it again to check if there is
some other issues.


**Second Attend**

*Time: 9216ms*

*Memory: 14.9 MB*

*Test Cases Passed: 54/54*


On my second attends, it successfully submitted it so we know that the only
thing we need to reduce the compiling time.


*I would suggest submit it more than once in case if you luckily have easier task cases*


![image](https://github.com/cywang95/images/blob/main/LeetCode/Q1-TwoSum/DoubleCheck.png?raw=true)

----

# Solution 2

**First Attend**

*Time: 564ms*

*Memory: 14.7 MB*

*Test Cases Passed: 54/54*


*Python3 Code*

```Python3
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        k = 0
        for i in nums:
            k += 1
            if target - i in nums[k:]:
                return(k - 1, nums[k:].index(target - i) + k)

```


*idea*
To avoid using two loops, we read each numbers and k will become an index of an
array. so `if target - i in nums[k:]:` *(need to use k:)* will let us know where
the number is located in the array.

![image](https://github.com/cywang95/images/blob/main/LeetCode/Q1-TwoSum/S2result.png?raw=true)

------

# Official Solution

**Two-pass Hash Table**
To improve our run time complexity, we need a more efficient way to check if the complement exists in the array.
If the complement exists, we need to look up its index. What is the best way to maintain a mapping of each element in the array to its index? A hash table.

We reduce the look up time from *O(n)* to *O(1)* by trading space for speed. A hash table is built exactly for this purpose, it supports fast look up in *near* constant time. I say “near” because if a collision occurred, a look up could degenerate to *O(n)* time. But look up in hash table should be amortized *O(1)* time as long as the hash function was chosen carefully.

A simple implementation uses two iterations. In the first iteration, we add each element’s value and its index to the table. Then, in the second iteration we check if each element’s complement *(target−nums[i])* exists in the table.

Beware that the complement must not be *nums[i]* itself!




*Python3 Code*

```Python3
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        hashTable = {}
        length = len(nums)
        for i in range(length):
            hashTable[nums[i]] = i

        for i in range(length):
            if target - nums[i] in hashTable and hashTable[target - nums[i]] != i:
                return [i, hashTable[target - nums[i]]]
        return([])
```

![image](https://github.com/cywang95/images/blob/main/LeetCode/Q1-TwoSum/twoPassHashTableResult.png?raw=true)





**One-Pass Hash Table**

It turns out we can do it in one-pass. While we iterate and inserting elements into the table, we also look back to check if current element’s complement already exists in the table.

If it exists, we have found a solution and return immediately.


*Python3 Code*
```Python3

class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        hashTable = {}
        for i, num in enumerate(nums):
            if target - num in hashTable:
                return([hashTable[target - num], i])
                break
            hashTable[num] = i
        return([])
```

However, the result isn't as impressive as Two-Pass Hash Table.


![image](https://github.com/cywang95/images/blob/main/LeetCode/Q1-TwoSum/OnePassHashTable.png?raw=true)



-----

# Conclusion

1. There are many solutions for this question, from using loops to hash table,
need to be familiar with basic ideas also need to know time complexity.
2. Need to improve Python3, still stuck on some syntax.
3. Didn't know anything about Hash Table, need to take a look of it

-----
*Date: 2021/7/9 11:50PM*

*Author: CYWang*
