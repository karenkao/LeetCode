# Linked list

linked list 跟 array 放在一起理解， 也會比較他們的優缺點

先說 array 一開始會宣告他有多長，所以儲存空間會連在一起，也因為這樣可以指定位置直接取他的 value ，例如我們會 array[0] = value，這就是他的優點。

那缺點是，因為他存放是緊密的，當我要對一個 array 操作時，例如： insert , delete，都會很麻煩，如果要插入一個值，我就需把一些移動到後面，在把那一格留給我要插入的值，刪除也是一樣的情況，我要刪除中間的其中一個數字，我就必須移除她，然後後面的值都要往前補充。

相反的 linked list 的優點跟缺點剛好跟 array 倒過來

先說 liked list 的方式，它每一個 node 存值和 liked 下一個是誰的功能，就像是火車一節一節的概念，所以當要對她操作的時候，只要改變 liked 的動作就可以了，像是我要delete 其中一個 node ，我就把 linked 到 next ，那中間那個值自然就被拋棄了。


## 放一張比較圖

![1_nDwDbeHwOz_Kl4zRIMbe_A](https://user-images.githubusercontent.com/88547312/157837644-2d8d54ee-5254-4053-9a5e-918f9457f233.png)


# 2 Simple Ways To Code Linked Lists



## first sample

先來製作 node 的部分，用一個 class 去定義他，它包含了 value 和 next 。

```python
class linkedListNode:
    def __init__(self, value, nextNode=None):
        self.value = value
        self.nextNode = nextNode

```

用範例來看這一個 class

1. 我們先創立三個 node ，分別為 3、7、10
2. 再來把 node 黏起來
3. 印出來看他!

```python
class linkedListNode:
    def __init__(self, value, nextNode=None):
        self.value = value
        self.nextNode = nextNode

node1 = linkedListNode("3")
node2 = linkedListNode("7")
node3 = linkedListNode("10")

node1.nextNode = node2
node2.nextNode = node3

currentNode = node1
while True:
    print (currentNode.value, '-> ',end="")
    if currentNode.nextNode is None:
        print('None!')
        break
    currentNode = currentNode.nextNode

```

印出來會長這樣:

3 -> 7 -> 10 -> None!

## Second sample

剛剛提到的是linked list 裡面 node 的部分，那完整的 linked list 其實還有 head，所以再來實作一個完整的 linked list class。

那他的邏輯就會是，一開始的 node class

然後新的 linkedlist class，它包含了 head 和 insert 的 function ，node 就呼叫原本的 那一個 classs 去定義他，接著去看 head 是不是 None ，如果是 None 則 head = node ，並且更因 currentNode 就是這個頭，最後去檢查next 是不是 None 如果是的話就跳出沒有的話就繼續等於下一個。

另外還寫了一個 print 的功能，比較好檢視他

```python

class linkedListNode:
	def __init__(self, value, nextNode=None):
		self.value = value
		self.nextNode = nextNode

class linkedList:
	def __init__(self, head=None):
		self.head = head

	def insert(self,value):
		node = linkedListNode(value)
		if self.head is None:
			self.head = node
			return
		currentNode = self.head
		while True:
			if currentNode.nextNode is None:
				currentNode.nextNode = node
				break
			currentNode = currentNode.nextNode

	def printLinkedList(self):
		currentNode = self.head
		while currentNode is not None:
			print( currentNode.value, ' -> ', end='')
			currentNode = currentNode.nextNode
		print('None!')

ll = linkedList()
ll.printLinkedList()
ll.insert("3")
ll.printLinkedList()
ll.insert("4")
ll.printLinkedList()
ll.insert("5")
ll.printLinkedList()

```

印出來會長這樣:

None!
3  -> None!
3  -> 4  -> None!
3  -> 4  -> 5  -> None!

## ref
- yt video : https://www.youtube.com/watch?v=-LmHUlozTqE
- medium https://medium.com/@tobby168/%E7%94%A8python%E5%AF%A6%E4%BD%9Clinked-list-524441133d4d
-  yt video (https://www.youtube.com/watch?v=6sBsF13n5ig&ab_channel=AnthonySistilli
