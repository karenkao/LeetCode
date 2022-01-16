# Valid Sudoku

這題要檢查它有沒有符合數獨的規則，數獨規則有三條:

1. row 不能重複
2. col 不能重複
3. 9 宮格 不能重複

(最後九宮格比較難寫)


```python

class Solution(object):
    def isValidSudoku(self, board):
        """
        :type board: List[List[str]]
        :rtype: bool
        """
        #依據三個條件檢查
    
        # row not duplicate 
        for i in range(9):
            tmp = board[i][:]
            tmp = [element for element in tmp if element !='.']
            if len(tmp) != len(list(set(tmp))):
                return False

        # col not duplicate
        for i in range(9):
            tmp = []
            for j in range(9):
                tmp.append(board[j][i])
            tmp = [element for element in tmp if element !='.']
            if len(tmp) != len(list(set(tmp))):
                print(False)
                return False

        # 3X3 not duplicate
        n = len(board)
        for r in range(0,n,3):
            for c in range(0,n,3):
                tmp = []
                for i in range(3):
                    for j in range(3):
                        tmp.append(board[r+i][c+j])
                tmp = [element for element in tmp if element !='.']
                if len(tmp) != len(list(set(tmp))):
                    return False  
        return True
        
```

把它們寫得整齊一點

```python
class Solution(object):
    
        #依據三個條件檢查
    
        # row not duplicate
        def isValidRow(self,board):
            for i in range(9):
                tmp = board[i][:]
                tmp = [element for element in tmp if element !='.']
                if len(tmp) != len(list(set(tmp))):
                    return False
            return True

        # col not duplicate
        def isValidCol(self,board):
            for i in range(9):
                tmp = []
                for j in range(9):
                    tmp.append(board[j][i])
                tmp = [element for element in tmp if element !='.']
                if len(tmp) != len(list(set(tmp))):
                    print(False)
                    return False
            return True

        # 3X3 not duplicate
        def isValidNineCell(self,board):
            n = len(board)
            for r in range(0,n,3):
                for c in range(0,n,3):
                    tmp = []
                    for i in range(3):
                        for j in range(3):
                            tmp.append(board[r+i][c+j])
                    tmp = [element for element in tmp if element !='.']
                    if len(tmp) != len(list(set(tmp))):
                        return False  
            return True
        
        def isValidSudoku(self, board):
            """
            :type board: List[List[str]]
            :rtype: bool
            """
            return self.isValidRow(board) and self.isValidCol(board) and self.isValidNineCell(board)
```


## 參考
- https://blog.csdn.net/fuxuemingzhu/article/details/82813653

