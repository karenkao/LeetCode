# Reverse Linked List

這題要 reverse linked list ，但又由於 linked list 的特性不能直接指向最後一個，所以要想一下


```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def reverseList(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        
        pred = None
        
        while head:
            
            Next = head.next
            head.next = pred
            pred = head
            head = Next
            
        return pred

```

## 交換法

用交換的方式，例如說有一個是 [1,2,3] => [3,2,1]

所以其實是 1 和 3 換位置，而在 linked list 原本的 3 要指向 None ，則反過來變成 1 指向 None

可以參考: https://ithelp.ithome.com.tw/articles/10271920

![image](https://user-images.githubusercontent.com/88547312/159167920-82abc9f7-1f12-4921-aac3-575a01c8897a.png)

原本的:

- head = 自己
- head.next = 下一個
- pred = 上一個

reverse 後:

- head = 下一個 (head.next)
- head.next = 上一個 (pred)
- pred = 自己 (head)

