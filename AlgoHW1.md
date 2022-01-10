

Zhengmao Zhang

Algo HW1

### Problem 1: Asymptotic Analysis Practice

##### (a) [5 points] Prove or disprove that logk n ∈ O(lg n) for any k > 1. (Note that lg refers to log2)

Answer:  Its True.  while K > 1( cuz K ∈ Z, so (K >=2) == (K > 1)), logk(n) = log2(n)/log2(k). cuz k > 1. we can see for every      k > 1( k >=2).  1/log2(k) <= 1 always hold. So let 1/log2(k) = c. we can get that logk(n) ≤ clog2(n) for any n. According to the defination, logk n ∈ O(lg n).

##### (b) [5 points] The following recurrence relation solves to O(n log2 n). Prove this using some variety of substition. Do not use the Master method.

##### T(n) = 2T(n/2) + n lg n

##### T(1) = 0

Answer:  let ![](/Users/zhengmao/Library/Application%20Support/marktext/images/2022-01-09-16-33-13-image.png)

![](/Users/zhengmao/Library/Application%20Support/marktext/images/2022-01-09-16-35-05-image.png)

let ![](/Users/zhengmao/Library/Application%20Support/marktext/images/2022-01-09-16-35-54-image.png)

![](/Users/zhengmao/Library/Application%20Support/marktext/images/2022-01-09-16-36-26-image.png)

![](/Users/zhengmao/Library/Application%20Support/marktext/images/2022-01-09-16-37-11-image.png)

![](/Users/zhengmao/Library/Application%20Support/marktext/images/2022-01-09-16-38-15-image.png)

therefore, we can get that 

![](/Users/zhengmao/Library/Application%20Support/marktext/images/2022-01-09-16-40-21-image.png)

So, 

![](/Users/zhengmao/Library/Application%20Support/marktext/images/2022-01-09-16-41-58-image.png)

It is ![](/Users/zhengmao/Library/Application%20Support/marktext/images/2022-01-09-16-42-31-image.png)

##### c) [5 points] Suppose that f(n) and g(n) are non-negative functions. Prove or disprove the following: if f(n) ∈ O(g(n)) then 2f(n) ∈ O(2g(n)).

Answer: The suppose is False. So we need disprove it.

let f(n) = 2n, if f(n) ∈ O(g(n)), we can get g(n) = n.

take  f(n) = 2n, g(n) = n into 2^f(n) ∈ O(2^g(n))

![](/Users/zhengmao/Library/Application%20Support/marktext/images/2022-01-09-23-31-44-image.png)is not work. so the supporse is False.

#### 2.

##### (a) [5 points] Give a linear time algorithm to solve this problem. (This should be obvious)

```pursudocode
res []
for i in arraryA:
    if a[i-1]<a[i]>a[i+2]
        return i
```

##### (b) [10 points] Give a ∈ O(log n) time algorithm to solve this problem.

```pusudocode
arr[] = [-2,6,-1,4,9,-5,5]
// for this func start, left should init 0, right should be the 
// size of the arr
func findPeak(left, right){
    mid = left + (high - left) / 2
    // if mid is left or right thats meaning we find
    if mid at left head OR mid at right tail
        return mid
    // if left half part is increasing, Peak should on left
    if arr[mid - 1] > arr[mid]
        return findPeak(left, (mid - 1))
    //else its on right half part
    return findPeak((mid -1), right)
}
```

##### (c) [10 points] What if instead of a simple array you are given a square matrix, where a Peak is now defined as an element larger or equal to its four neighbours. Give a O(n log n) solution to this variant of the problem.

```psedocode
findPeakInMatrix(){
        low = 1
        high = A.length - 2

        while(low <= high){

            mid = low + (high - low) / 2
            // its find Peak in 2D arr, we can just use b)'s func
            col = findPeak(0, A[0].size)
            if(A[mid][col] < A[mid - 1][col]){
                high = mid - 1;
            }else if(A[mid][col] < A[mid + 1][col]){
                low = mid + 1;
            }else{
                return [mid, col]
            }
        }
}
```


