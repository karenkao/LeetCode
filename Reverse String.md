# Reverse String

這題 reverse string，而且不使用額外的空間

```python
class Solution:
    def reverseString(self, s: List[str]) -> None:
        """
        Do not return anything, modify s in-place instead.
        """
        for i in range(int(len(s)/2)):
            tmp = s[i]
            s[i] = s[len(s)-i-1]
            s[len(s)-i-1] = tmp
```


