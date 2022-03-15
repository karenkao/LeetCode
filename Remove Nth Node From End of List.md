# Remove Nth Node From End of List

## 題目

這題是給一個 linked list 和 n ， return 刪除倒數n的數字後的 linked list。

## 思路：

要做兩個版本的，一個是先不考慮時間複雜度的直覺解，另外一個是要考慮不能超過 time limit。

- first solution  

```python 
class Solution:
    def removeNthFromEnd(self, head: Optional[ListNode], n: int) -> Optional[ListNode]:
        
        count_head, count_node = head, head
        len_linkedlist = 1
        
        while count_head.next is not None:
            len_linkedlist +=1
            count_head = count_head.next
            
        
        for i in range(len_linkedlist-n-1):
            count_node = count_node.next
        count_node.next = count_node.next.next
        return head

```

這裡的想法是，先算 linked list 的 len ，所以把 linked list 複製一份，然後 while 到當它下一個是  None 的時候，就停下來此時計算總共有多長，知道多長後就可以把倒數 n remove，倒數 n remove 這邊有點特別，去修改原本複製的 count_node ，她也會去改變 head ，所以最後是 return head 。

### 這個新發現可以參考： https://leetcode.com/explore/interview/card/top-interview-questions-easy/93/linked-list/603/discuss/8802/3-short-Python-solutions

來自 Andyinyang 8  October 4, 2021 2:14 PM 的回覆

Python copy assignments are essentially pointers to the reference (in this case head). So changing slow, also changes head. However since the original head pointer is to its 'head', we can simply return that as desired with the reflected changes from mutating slow.

也就是說我們在一開始的

count_head, count_node = head, head

count_head和 count_node 會連動到 head ，平常的 list 如果用這樣的方式複製也會連動到原本的，除非用 .copy。

```python
a = [1,2,3,4]
c ,d = a.copy(), a.copy()
c[0] = 444
print(c)
print(a)

Finished in 61 ms
[444, 2, 3, 4]
[1, 2, 3, 4]

```

```python
a = [1,2,3,4]
c ,d = a, a
c[0] = 444
print(c)
print(a)

Finished in 63 ms
[444, 2, 3, 4]
[444, 2, 3, 4]

```
