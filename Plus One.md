# Plus One

https://leetcode.com/explore/interview/card/top-interview-questions-easy/92/array/559/

這是把數字塞進去陣列裡面，也是十進位制的，然後要替這個數字陣列加一

這裡學到 for loop reverse

```python
# 如果加一會大於 9 ，則這個數字要等於 10 ，然後進位 1 ，直到跑完整個 for loop
# 如果跑完整個 for loop ，進位還是 1 則前面要加一位數，例如 999 三位數，加上 1 ，變成 1000 就是四位數


class Solution:
    def plusOne(self, digits: List[int]) -> List[int]:
        plus =1
        for i in range(len(digits)-1, -1 ,-1):
            if digits[i] + plus >9:
                digits[i] = 0
                plus = 1
            else:
                digits[i] += plus
                plus = 0
        if plus == 1:
            digits.insert(0,1)
        return digits

```

[https://blog.csdn.net/coder_orz/article/details/51583916](https://blog.csdn.net/coder_orz/article/details/51583916)


```python
# 這裡簡化成不用每個都改，就是只要知道那個值有沒有小於 9

class Solution:
    def plusOne(self, digits: List[int]) -> List[int]:
				plus =1
				    
				    for i in range(len(digits)-1, -1 ,-1):
				        if digits[i] < 9:
				            digits[i] += 1
				            
				            return digits
				        else:
				            digits[i] =0
				            
				    digits.insert(0,1)
				    
				    return digits
```
