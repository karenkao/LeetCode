#  String to Integer (atoi)


```python
class Solution:
    def myAtoi(self, s: str) -> int:
        s = s.replace(" ", "")
        output_arr = []
        for i in range(len(s)):
            if not s[i].isalpha():
                output_arr.append(s[i])

        if output_arr[0] =='-':
            flag = -1
            output_arr = output_arr[1:]
        else:
            flag = 1

        output = 0
        # check '.'

        if '.' in output_arr:
            index = output_arr.index('.')
            output_arr_left = output_arr[0:(index)]
            output_arr_right = output_arr[(index+1):]

            for m in range(len(output_arr_left)):
                output += int(output_arr_left[m]) * (10**(len(output_arr_left)-m-1))

            for n in range(len(output_arr_right)):
                output += round(int(output_arr_right[n]) * (0.1 **(n+1)),(n+1))
            output = round(output,(n+1))

        else:
            for j in range(len(output_arr)):
                output += int(output_arr[j]) * 10**(len(output_arr)-j-1)
        output *= flag
        return output        
```

