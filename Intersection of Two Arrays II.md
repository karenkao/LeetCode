# Intersection of Two Arrays II

要找兩個陣列的交集，特別注意此兩陣列其中是可以重複的(所以 set 不管用...)


直覺的方法，用一個陣列的 item 去找另外一個陣列有沒有這個元素，有的話加入output並且 remove

```python
class Solution(object):
    def intersect(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: List[int]
        """
        output_arr = []
        for item in nums1:
            if item in nums2:
                output_arr.append(item)
                nums2.remove(item)
        return output_arr
        
```        

放在 dict  去做，且dict 去算元素的 frequency ，所以那一個元素就不會被重複處理到，也可以用兩陣列變成的 dict 去看他的 frequency 取min 就是 output 的
```python
class Solution(object):
    def intersect(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: List[int]
        """
    
        output_arr = []
        count1 =  collections.Counter(nums1)
        count2 =  collections.Counter(nums2)

        for key, value in count1.items():
            if key in count2:
                output_arr += [key]*min(value,count2[key])
        return output_arr
``` 
        
再加快一些

```python 
class Solution(object):
    def intersect(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: List[int]
        """
    
        output_arr = []
        count1 =  collections.Counter(nums1)
        count2 =  collections.Counter(nums2)

        return (count1 & count2).elements()
``` 
