# Implement strStr()

needle in a haystack 大海撈針

給定兩個字串，一個表示大海，一個表示針，如果針在大海裡面，回傳第一個針的 index，如果不在的話  return -1 。

其中注意邊界值，如果針為 空字串，


```Python
class Solution:
    def strStr(self, haystack: str, needle: str) -> int:
         
        if needle in haystack:
            return haystack.index(needle)
        else:
            return -1
```
