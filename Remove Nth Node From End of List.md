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
回到題目，還有一個邊界值要考慮，有幾個可能：

1. n  = len(linkedlist)  => 那這個就是第一個值被跳過，直接下一個
，再 retrun head 
2. n  > len(linkedlist)  => 題目限制沒有這種
3. n  < len(linkedlist)  => 這個已經完成

所以修改後完整的第一板是：

```python

class Solution:
    def removeNthFromEnd(self, head: Optional[ListNode], n: int) -> Optional[ListNode]:
        
        count_head, count_node = head, head
        len_linkedlist = 1
        
        while count_head.next is not None:
            len_linkedlist +=1
            count_head = count_head.next
            
       
        if n == len_linkedlist:
            head = head.next
            return head
        else:
            
            for i in range(len_linkedlist-n-1):
                count_node = count_node.next
            count_node.next = count_node.next.next
            return head

```

因為第一版會超過時間，所以要來想第二個版本，第一版的 loop 要跑兩次，一次跑計算總長 len ，第二次是看倒數幾個，那把 loop 兩次減半就可以加速了。

所以這樣做， 有兩個 pointer 的概念，一個是 fast pointer 和 slow pointer， 他們兩個差 n step 出發，也就是說 fast pointer first tow go ，but slow pointer waits n step then go ，
跑完全部(也就是 next = None 的時候) ，fast 走到最後了， slow 就會是他要被跳過的也就是倒數 n 個，那這裡直接做 remove 的動作，我們的 loop 就不用跑兩次~

最後要檢查一個情況是， fast 跑到最後但是 slow 還沒出發也就是在第一個位置，這個時候就是 return head = head.next

- second solution 

```python 
class Solution:
    def removeNthFromEnd(self, head: Optional[ListNode], n: int) -> Optional[ListNode]:
        
        fast_node, slow_node = head, head
        count = 0
        while fast_node.next is not None:
                
            fast_node = fast_node.next
            count += 1

            if count == n:
                slow_node = head
            elif count > n:
                slow_node = slow_node.next
                
        if count < n:
            head = head.next
            return head
        else:
            slow_node.next = slow_node.next.next  
        return head
     
```


- share my solution in python on leetcode : https://leetcode.com/explore/interview/card/top-interview-questions-easy/93/linked-list/603/discuss/1851161/my-solution-in-python
