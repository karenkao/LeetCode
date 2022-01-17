# Reverse Integer

這提要 reverse integer ，而且有可能為負值，另外多一個最大值的限制，如果超過最大值 return 0

解題的方法是
1. 先紀錄下正負號在 flag
2. 再把 integer to str to list
3. reverse by list , 就當做是 array 在轉換
4. 加回去正負號，乘以 flag
5. 確認是否超過限制後 return 

``` python 
class Solution:
    def reverse(self, x: int) -> int:
        if x < 0:
            x =  str(-x)
            flag = -1
        else:
            flag = 1
        x = list(str(x))

        for i in range(int(len(x)/2)):
            tmp = x[i]
            x[i] = x[len(x)-i-1]
            x[len(x)-i-1] = tmp

        output = 0
        for j in range(len(x)):
            output += int(x[j])* (10**(len(x) - j-1))
            
        output = output * flag
        # Check if the result is within MaxInt32 and MinInt32 bounds
        min_int_32 = 2 ** 31
        if output <= -min_int_32 or output >= min_int_32-1:
            return 0
        else:
            return output
```
