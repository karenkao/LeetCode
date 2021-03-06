# Delete Node in a Linked List

開始 linked list topic 了！看一些參考資料了解一下 linked list 的原理

影片原理說明可以看這個 : https://www.youtube.com/watch?v=-LmHUlozTqE

## 影片 brief 
linked list 跟 array 放在一起理解， 也會比較他們的優缺點

先說 array 一開始會宣告他有多長，所以儲存空間會連在一起，也因為這樣可以指定位置直接取他的 value ，例如我們會 array[0] = value，這就是他的優點。

那缺點是，因為他存放是緊密的，當我要對一個 array 操作時，例如： insert , delete，都會很麻煩，如果要插入一個值，我就需把一些移動到後面，在把那一格留給我要插入的值，刪除也是一樣的情況，我要刪除中間的其中一個數字，我就必須移除她，然後後面的值都要往前補充。

相反的 linked list 的優點跟缺點剛好跟 array 倒過來

先說 liked list 的方式，它每一個 node 存值和 liked 下一個是誰的功能，就像是火車一節一節的概念，所以當要對她操作的時候，只要改變 liked 的動作就可以了，像是我要delete 其中一個 node ，我就把 linked 到 next ，那中間那個值自然就被拋棄了。

放一張我覺得的最好的比對圖：

![1_nDwDbeHwOz_Kl4zRIMbe_A](https://user-images.githubusercontent.com/88547312/157839402-03640f81-5e16-4857-a925-102ef6c186ad.png)


## 解題

這一題他要刪除一個元素，通常都是給要刪除的前一個，然後直接連結到要刪除的後一個，但她卻是給要刪除的那一個，那就是要把要刪除的下一個就變成這一個，要刪除的下一個變成下下個。


```python
# # Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def deleteNode(self, node):
        """
        :type node: ListNode
        :rtype: void Do not return anything, modify node in-place instead.
        """
        
        node.val = node.next.val
        node.next = node.next.next
```
