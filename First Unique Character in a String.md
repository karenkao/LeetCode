# First Unique Character in a String

這題要找到第一個不重複的字母，回傳那個字母的 index，如果每個字母都重複因此沒有找到回傳 -1


```Python
class Solution:
    def firstUniqChar(self, s: str) -> int:
        counter=collections.Counter(s)
        for key,value in counter.items():
            if value == 1:
                return s.index(key)
        else:
            return -1
```
