# Q26: Remove Duplicated From Sorted Array

**Level: Easy**

---

**Solution**

```Python3

k = 0
if len(nums) == 0: return k

for i in range(1, len(nums)):
  if nums[k] < nums [i]:
  k += 1
  nums[k] = nums[i]

return k+1
```
---

*Date: 2022/06/16*

*Author: CYWang*
