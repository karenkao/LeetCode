# Power of Three

這題是看他是不是3 的次方數


```python
class Solution(object):
    def isPowerOfThree(self, n):
        """
        :type n: int
        :rtype: bool
        """
        # n = abs(n)
    
        if n <=0:
            return False

        if n ==1 :
            return True


        while n%3 == 0:
            n/=3
        return n ==1
```

解題的想法是:

1. 如果他小於 0 return False
2. 如果他 ==1 return True
3. 如果他除以3 餘數為0 ，也就是能被3 整除，就一直除3 除到不等於0 的時候
4. 如果這時候他等於 1 代表他是 3 的次方數，但如果這時候不等於 1 代表 False
