#  Remove Duplicates from Sorted Array

這題要移出重複的元素從一個已經排序的陣列當中，但是加上一個限制是 in-place，不能使用額外的空間(所以變得有點麻煩...)

**一開始想到的版本，但不通過，應該是額外使用了空間!**

```python
nums = list(set(nums))
return len(nums)
```

所以換成用 pointer 的方式

我們用一個tmp 的和一個 pointer， pointer 一個一個輪當他和 tmp 不同時(也就是跳過重複的了)這時候陣列就要等於它，而這個pointer 剛好也代表長度

```python

class Solution(object):
    def removeDuplicates(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        
        pointer = 0
        tmp_number = None

        for num in nums:
            if num != tmp_number:
                nums[pointer] = num
                pointer +=1
                tmp_number = num
        return pointer
```
