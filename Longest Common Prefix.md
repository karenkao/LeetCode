# Longest Common Prefix

這題輸入多個字串，比較每個字串相同的部份，由字首開始，如果不同即跳出 ， prefix 前贅詞的概念。

所以邊界值，如果輸入的多個字串包含空字串，即回傳空字串。

以及如果皆沒有相同的字首時，也回傳空字串。

```Python
class Solution:
    def longestCommonPrefix(self, strs: List[str]) -> str:
        
        if "" in strs:
            return ""
        else:
            min_str = min(strs, key=len)


            for str_ in strs:
                if not str_[0] == min_str[0]:
                    return ""

            flag = -1
            for i in range(len(min_str)):
                for j in range(len(strs)):


                    if strs[j][i] == min_str[i]:
                        continue
                    else:
                        return min_str[:i]
            return min_str[:]
```
