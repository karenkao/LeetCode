# Valid Anagram

Anagram 指的是同字母異順序

題目會輸入兩個 str : s 和 t， 其中 t 要是 s 的Anagram ，也就是說 t 的所有組成要都存在於 s 當中。

```Python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        if not len(s) == len(t):
            return False
        
        counter_s = collections.Counter(s)
        counter_t = collections.Counter(t)
        
        for key,value in counter_t.items():
            if counter_s[key] != value:
                return False
        else:
            return True
        

```
