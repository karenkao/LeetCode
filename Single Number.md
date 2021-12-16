# Single Number

https://leetcode.com/explore/interview/card/top-interview-questions-easy/92/array/549/

要找出陣列中只有出現一次的

```python
# first submit
	# 用 coleection 套件，套件會列出每個元素有出ㄒ
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        elements_count = collections.Counter(nums)
        return [key for key in elements_count if elements_count[key]==1][0]

```

```python
# 比上一版更加速一些些
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        return  2*sum(set(nums)) - sum(nums)
```

```python
# 用 operator 但沒有比較快
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        a = 0 
        for num in nums:
            a ^= num
        return a
```

## operator ref

https://docs.python.org/zh-cn/3/library/operator.html

![image](https://user-images.githubusercontent.com/88547312/146378683-d415695b-a737-4b62-a054-12762ee3b505.png)

![image](https://user-images.githubusercontent.com/88547312/146378641-bf15fd1f-f633-4742-9282-53be4729598a.png)

主要使用 XOR ， XOR 就是 ^= ，XOR 的作用是如果當 3 ^= 0 會等於 3 ， 3 ^= 3 會等於 0
