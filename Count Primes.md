# Count Primes

這題要計算有多少個質數，一開始寫的土炮法會運行超過時間，後來 google 有一個厄拉多塞篩法，改之後才通過。


## 土炮法

思路是：有一個判斷她是否為質數的 function ，然後一開始的特殊情況如果為 0 或是 1 就直接 return 0，再來是有質數出現的情況，也就是 n> 2 以後，先創立一個 list 長度為 n 內容都是 true 的 list，然後在0 和1 更改為 false，接下來 for loop 每一個去判斷是不是為質數，如果是質數要將此數的倍數都註解為 false，且這個註解的過程有小 tips，他是一個 for loop 且開始於 i*i 就是當平方且到 n 的時候，然後每次移動都是 i 個距離，最後在 return sum True 的總和就是答案了。

但是這個的結果   Time Limit Exceeded  Last executed input:1500000

```python
#  Time Limit Exceeded  Last executed input:1500000

lass Solution:
    def countPrimes(self, n: int) -> int:
        

        def isPrime(number):
            if number == 0 or number ==1 :
                return 0
            elif number ==2:
                return 1
            else:

                for i in range(1,number,1):
                    if i * i <= number:
                        if i == 1:
                            continue
                        elif number % i == 0:
                            return 0
                    else:
                        return 1

        
        if n ==0 or n==1 :
            return 0
        else:
            output_list = [True]*n
            output_list[0],output_list[1] = False, False

            for i in range(n):
                if isPrime(i):
                    output_list[i] = True

                    for j in range(i*i,n,i):
                        output_list[j] = False
                else:
                    output_list[i] = False
            return sum(output_list)
        
```

## 所以加速一些的版本是

思路： 跟剛剛的想法很像，可是省去了判斷的 fuction 但因為有兩個 loop 所以還是比較慢

```python 

class Solution:
    def countPrimes(self, n: int) -> int:
        if n < 3:
            return 0
        primes = [True] * n
        primes[0] = primes[1] = False
        for i in range(2, n):
            if primes[i]:
                primes[i] = True
                for j in range(i*i,n,i):
                    primes[j] = 0
               
        return sum(primes)


```

## 目前最快的

```python 
 class Solution:
    def countPrimes(self, n: int) -> int:
         if n < 3:
                return 0
            primes = [True] * n
            primes[0] = primes[1] = False
            for i in range(2, int(n ** 0.5) + 1):
                if primes[i]:
                    primes[i * i: n: i] = [False] * len(primes[i * i: n: i])
            return sum(primes)
```
