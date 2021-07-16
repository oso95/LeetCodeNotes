# Q14: Longest Common Prefix

**LeveL: Easy**

----

**Solution 1**

```Python3

result = ""
ctr = 1
i = 1
index = len(strs[0])
isMatched = False

while ctr < index + 2:

    #break if strs only contain one string
    if len(strs) == 1:
        result = strs[0]
        isMatched = True
        break

    #check if i and ctr are in range
    if i+1 > len(strs):
        i = 1
        ctr += 1

    #return true if they are the same
    if strs[0][0:ctr] == strs[i][0:ctr] and ctr <= index+1:
        isMatched = True
        i += 1


    #return false if they are not the same
    elif strs[0][0:ctr] != strs[i][0:ctr] and ctr <= index + 1:
        isMatched = False
        i += 1

    #check if continue
    if i == len(strs) and isMatched:
        result = strs[0][0:ctr]
    elif i == len(strs) or not isMatched:
        break


return result

```

**idea**

Vertical scanning with while and if statement.


![image](https://github.com/cywang95/images/blob/main/LeetCode/Q14-Longest%20Common%20Prefix/Q14solution1.png?raw=true)

![image](https://github.com/cywang95/images/blob/main/LeetCode/Q14-Longest%20Common%20Prefix/3submissions%20result.png?raw=true)
