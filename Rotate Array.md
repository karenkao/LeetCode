# Rotate Array

旋轉 array ，依據 k 幾次轉幾次

解題時要注意，因為轉的次數等於陣列長度時，陣列就會回到原始狀態，所以可以用 k 跟陣列長度取餘數，用這個餘數當作轉幾次去做

```
class Solution(object):
    def rotate(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: None Do not return anything, modify nums in-place instead.
        """
        k =k% len(nums)
        nums[:] = nums[-k:] + nums[:-k]
```        
