# Move Zeroes

https://leetcode.com/explore/interview/card/top-interview-questions-easy/92/array/567/

這題要看把陣列中的0 移動到最後面，而且不增加額外的空間，不 return 

```python
# 一開始直覺想到的方法
# 但是這個比較慢
# 看有幾個 0 把他們都刪除
# 在陣列最後在加入 0
# 但是題目有兩個額外的限制
# 不要增加空間 且 要覆蓋原本的 arr 不是用 return 的方式
class Solution(object):
    def moveZeroes(self, nums):
        append_times=nums.count(0)
        for i in range(append_times):
            nums.remove(0) 
            nums.append(0)
```

```python
# 這個比較快 用兩個 point 的方式
# point 去判斷如果是 0 他是要被移動到後面的
# 所以看下一個是不是 0 如果是 0 互換沒有意思 去換下一個直到不是 0 的
# 然後一直往下 
# 直到 point 指到最後一個
class Solution(object):
    def moveZeroes(self, nums):
        if  len(nums) > 1:
            point_x = 0
            point_y = 1

            while point_y <= len(nums)-1:
                if nums[point_x] == 0 :
                    if nums[point_y] ==0:
                        point_y += 1

                    else:
                        nums[point_x] = nums[point_y]
                        nums[point_y] = 0
                else:
                    point_x +=1
                    point_y +=1
```
