# Roman to Integer

```python

class Solution(object):
    def romanToInt(self, s):
        """
        :type s: str
        :rtype: int
        """
        roman_dict = {}
        roman_dict["I"] = 1
        roman_dict["V"] = 5
        roman_dict["X"] = 10
        roman_dict["L"] = 50
        roman_dict["C"] = 100
        roman_dict["D"] = 500
        roman_dict["M"] = 1000
        index = 0
        total = 0
        while index <= len(s) -1:
            if index < len(s)-1:
                if s[index] == "I" and (s[index+1] == "V" or s[index+1] == "X") :
                    total += int(roman_dict[s[index+1]]) - int(roman_dict[s[index]])
                    index += 2
                elif s[index] == "X" and (s[index+1] == "L" or s[index+1] == "C"):
                    total += int(roman_dict[s[index+1]]) - int(roman_dict[s[index]])
                    index += 2
                elif s[index] == "C" and (s[index+1] == "D" or s[index+1] == "M"):
                    total += int(roman_dict[s[index+1]]) - int(roman_dict[s[index]])
                    index += 2
                else:
                    total += int(roman_dict[s[index]])
                    index += 1
            else:
                total += int(roman_dict[s[index]])
                index += 1
                
        return total



```       

羅馬數字題
這題一開始想用 for loop 去寫，但是後來遇到當兩個數字組合在一起可能會有減法的問題，所以要判斷他後面還有沒有字，且又是特定的數字的時候要做減法，減完之後就移動兩個，那這樣子的話for loop 就比較不適合，所以用 index 的方式去做，有點像是 pointer ，這樣可以 move one step or move two step 就很方便。
