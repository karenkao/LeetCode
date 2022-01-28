# Valid Palindrome

Palindrome 回文


這題要判斷輸入是不是一個回文，輸入的時候會有標點符號，例如逗點，要先把標點符號去除後判斷其是否為回文。

以及一個極端值，如果為空字串也是回文。

```Python 

class Solution:
    def isPalindrome(self, s: str) -> bool:
        s = s.replace(" ","")
        s = s.lower()
        if len(s) == 0:
            return True
        else:
            tmp = []
            for i in range(len(s)):
                if s[i].isalpha() or s[i].isdigit():
                    tmp.append(s[i])
        # print(tmp)
        for j in range(int(len(tmp)/2)):
            if tmp[j] != tmp[len(tmp)-j-1]:
                return False
        else:
            return True
            
```
