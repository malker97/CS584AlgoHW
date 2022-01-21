##### HW2

##### Zhengmao Zhang

#### Problem 1: Jarvis March (Gift Wrapping Algorithm)

##### (a) [10 points] Give pseudocode describing the Jarvis March algorithm, a brief description of how it works, and explain its best and worst case efficiency.

Answer: 

```pseudocode
algorithm Grahamscan(S) -> res is
	// S is the set of points S is S[x][y] set
	// res is the opint 
	res = []
	n = S.size() // n is number of all points
	
	// in this part we need find the lowest point, OR
	// highest point
	leftstPoint = S[0] //its start point
	for s in all S do
		leftestPoint = lefterPoint(lowestPoint, s)
	
	// this part will triversal all point set
	firstPoint = leftestPoint
	secondPoint = NULL
	repeat:
		res.push(firstPoint)
		secondPoint = S[firstPoint.Next]
		for s in S do
			if counterClockWise(firstPoint, s, secondPoint) do
				secondPoint = s
		firstPoint = secondPoint
 until firstPoint == leftestPoint
// this function is to test if the point s is in the line (that point1 and point2 connect) left
function counterClockWise(point1, point s, point2) -> bool do
	return ((point2.x - point1.x) * (s.y - point1.y) - (point2.y - point1.y) * (c.x - point1.x)) < 0
```

**TIME COMPEXITY** **O(nh )** h is the convex hull size

Worst Case **Θ(n^2)**

Best case **O(nh)** h is the convex hull

for the **best case**, the convex hull is a triangle, and only have 3 point on hull.

for the **worest case**, its all points are in solution hull.

![image-20220116234735028](/Users/zhengmao/Library/Application Support/typora-user-images/image-20220116234735028.png)



##### (b) [5] points Give an example input on which Jarvis March will perform significantly better than Graham’s scan and explain why it will perform better.

Answer:

Data Set: [[0,0] , [100, 0], [0, 100], [1,1],[2,2], [3,3], [4,4]……[49,49], [50,25], [25,50], [25,37.5], [37.5,25]]

There are 3 lines in the data set, one is X=Y, another is [50,0]->[0, 100], and [0,50] -> [100,0]

for this data set, the convex hall is {[0,0], [100, 0], [0,100]}

for the **Jarvis March** , this data set is best case for Jarvis March. the complelity is O(hn), h = 3. Its almost to O(n)

for the **Graham’s scan**,it is worest case for it, cuz there are 3 lines start at convex hall. So in the algorithm. the complexity is O(n log n)



##### (c) [5] points Give an example input on which Graham’s Scan will perform significantly better than Jarvis March and explain why it will perform better.

Data set: [[0, 0], [1,0], [2,0], [3, 0]……[100,0]], [, [0,1], [0,2], [0,3]……[0,100]], [[99, 1],[98, 2], [97,3], ……[1,99]]

In this data set, the convex hall is all points in this set.

for the **Jarvis March** , this data set is worst case for Jarvis March. cuz the h is n, so the complexity is O(n^2)

for the **Graham’s scan**,it is best case for it, cuz there are 3 lines start at convex hall. So in the algorithm. the complexity is O(n log n)

#### Problem 2: Find the Missing Number

##### (a) [5 points] Give an efficient algorithm for finding the missing number, show its complexity, and argue its correctness. (You should try for O(n)-time, less efficient solutions will still get partial credit)

Answer:

if its a sorted list, we can just do a compare function to make a[i] compare with i.

```pseudocode
dataSet = []
algorithm getMissingNumber() is:
	// n is the size of arr DataSet
	n = dataSet.size
	for i from 0 to n - 1 do
  	if dataSet[i] is not i then
  		// attention: should return i, its not dataSet[i], cuz dataSet i is exist
  		return i
	
```

In this algorithm, its ofc **O(n)** cuz its only one loop from 0 to n, so its **O(n)**

if its a **unsorted** list, we need get the sum of range n - 1

```pseudocode
dataSet = []
algorithm getMissingNumber() is:
	// n is the size of arr dataSet
	n = dataSet.size
	sum = 0
	for i in range(0, n - 1) do
		sum += i
	for each dates in dataSet do
		sum -= dates
	return sum
```

Its **O(n)**, cuz the get sum part is **O(n)**, and the search part is **O(n)**, so its **O(n)**

##### 

Answer: Use XOR operator.

```pseudocode
dataSet = []
algorithm getMissingNumber() is:
	// n is the size of arr dataSet
	n = dataSet.size
	
	x1 = dataSet[0]
	x2 = 1
	for i in range(0, n - 2) do
		x1 = x1 XOR dataSet[i]
	for i in range(1, n - 1) do
		x2 = x2 XOR dataSet[i]
	return x1 XOR x2
	
```

cuz XOR can delete repeat number. 

> like x1 = x2 XOR x3
>
> if we wanna get the x2, we can just x1 XOR x3

for complexity, TIME is O(n), NSPACE is O(1). Cuz for the 1st XOR loop, its O(n), the 2nd same. So its O(n)



##### (b) [10 points] For this question you are not allowed to access an entire integer with a single operation. The elements of the list are represented in binary, and the only operation you can use to access them is GetBinaryDigit(A[i],j) which returns the jth bit of element A[i] which runs in constant time. Give an efficient algorithm for finding the missing number under these constraints, show its complexity, and argue its correctness. (You should try for O(n)-time and O(log n)-space, less efficient solutions will still get partial credit)

##### Example: If we run GetBinaryDigit(A[i],j) with A[i] = 29 and j = 2, it would return a 0 since 29 = 11101.

Answer:

If the data set is a sorted

```pseudocode
A = []
algorithm getMissingNumber() is:
	prelastdig = 1
	for i in range(n):
		if(GetBinaryDigit(A[i],2).lastdig == prelastdig)
			return A[i] - 1
```

If its not sorted.

for this problem, we can know, for every n size set, we get the unsigned number num[i]'s length in binary, the max length of nums[i]ToBi.toString.length is lg(n + 1) - 1. so we need find the solution in this part. 

```pseudocode
algorithm getMissingNumber(subarr, n) is:
	if n is 1
		return 1 - subarr[0]
		leftsubarr = []
		rightsubarr = []
		highersite <- ceiling( lg(n+1) ) - 1
		for all num in subarr do
			if num[highersite] is 0 do
				leftsubarr.append(num)
			else
				rightsubarr.append(num)
		if leftsubset.size() < pow(highersite, 2)
			getMissingNumber(leftsubarr, pow(highersite, 2) - 1)
		else
			getMissingNumber(rightsubarr, n - pow(highersite, 2))
```

 **PSPACE(LogN)**, cuz its a recurssion function. so we find they always have the half size of current sub arr, so its run in Log n **SPACE**

For the **PTIME(N)**, we can get the size of input is (2^(log (n + 1) - 1)) - 1

then we can get **T(n)** <= T((2^lg (n + 1)) - 1)

cuz 2^ lg(n + 1)  ≈ n

T(n) = aO(n) - T(1) = **O(n)**