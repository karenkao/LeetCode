# Best Time to Buy and Sell Stock II

https://leetcode.com/explore/interview/card/top-interview-questions-easy/92/array/564/

找到最大利益，低買高賣

```python

# 因為不一定要每天買跟賣，可以第一天買，最後一天賣
# 所以有一個其他的概念產生，可以全部買全部賣
# 只要明天比今天高價，今天就可以買
# 如果第三天比第二天高價，則第三天也要買，第二天可以賣掉
# 所以唯一要檢查的事情是，明天有沒有比今天高價
# 如果有比今天高價就要買賣
# 且利益是明天的價錢減去今天的

class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        profit = 0
        
        for i in range(len(prices) -1):
            if prices[i+1] > prices[i]:
                profit += prices[i+1] - prices[i]
        return profit
```

[https://blog.csdn.net/fuxuemingzhu/article/details/70258549](https://blog.csdn.net/fuxuemingzhu/article/details/70258549)
