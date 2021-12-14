# Two Sum

[https://leetcode.com/problems/two-sum/](https://leetcode.com/problems/two-sum/)

```python
# first submit
# 用減法去看需要的值有沒有在剩下的 list 裡面
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        
        for i in range(len(nums)):
            complement = target - nums[i]
            
            if complement in nums and nums.index(complement) != i:
                return [i, nums.index(complement)]
```

```python
# second submit
# 先用一個 for loop 把裡面的list 存成dict 用key 和 value 找速度比較快
# 取代原本用 index 找的方式
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        hashmap = {}
        for i in range(len(nums)):
            hashmap[nums[i]] = i
        for i in range(len(nums)):
            complement = target - nums[i]
            if complement in hashmap and hashmap[complement] != i:
                return [i, hashmap[complement]]
```

```python
# third submit
# 上一版的兩個 for loop 改成只有一個
# 不符合的就加入 dict 裡面
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        myHash = {}
        for index, value in enumerate(nums):
            if target - value in myHash:
                return [myHash[target-value], index]
            myHash[value] = index
```
