# Rotate Image

這題要旋轉矩陣，其實就是平常在使用 opencv的功能 rot_90、 rot_180，變成手刻的這樣。

那這題參考: https://youtu.be/8YFV_LTs8ng

他的思路有兩個步驟:

1. 先製作轉置矩陣
2. reverse list


``` python 
class Solution(object):
    def rotate(self, matrix):
        """
        :type matrix: List[List[int]]
        :rtype: None Do not return anything, modify matrix in-place instead.
        """
        for row in range(len(matrix)):
            for col in range(row,len(matrix)):
                print(matrix[row][col])
                matrix[row][col],matrix[col][row] = matrix[col][row], matrix[row][col]
        for i in range(len(matrix)):
            matrix[i].reverse()


```
