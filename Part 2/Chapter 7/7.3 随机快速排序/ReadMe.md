随机快速排序 算法
===========

算法概览
---------

**随机快速排序**算法 要解决的问题是要解决的问题是 排序问题，以下是排序问题的说明：

输入：n个数的一个序列<a1，a2，...，an>

输出：输入序列的一个排列<a1'，a2'，...，an'>，满足a1'<=a2'<=....<=an'。

通常情况下随机快速排序平均性能非常好，是排序实际应用的最好选择之一。

与快速排序一样，随机快速排序也使用了分治的思想。随机快速排序仍然把待排序数组A[p..r]分成两个子数组，

A[p..q-1]和A[q+1..r]，使得A[p..q+1]中的每一个元素都比A[q]小（或相等），使得A[q+1..r]中的每一个元素都比A[q]大（或相等），

**唯一和快速排序不同的是，枢轴q的选择是随机的**，

这个算法通过递归的调用随机快速排序，再接着分别对A[p..q-1]和A[q+1..r]进行排序，最后使A[p..q]整体有序。

算法性能
---------

最坏情况下时间复杂度：O(n^2)。

平均/期望的时间复杂度：O(nlgn)。

算法伪代码
-----------

```
RANDOM-QUICKSORT(A, p, r)
	if q < r
		q = PARTITION(A, q, r)
		QUICKSORT(A, p, q-1)
		QUICKSORT(A, p+1, r)
```

```
PARTITION(A, q, r)
	从q..r之间随机找一个数和A[r]的值互换
	x = A[r]
	i = p - 1
	for j = p to r - 1
		if A[j] <= x
			i = i + 1
			交换A[i]和A[j]
	交换A[i+1]和A[r]
	return i + 1
```

书上原版的算法伪代码
-----------------------
//以下是书上写的伪代码，不过我们觉得上面的写法比较直观。
//RANDOM(q, r)是一个函数，这个函数在q~r之间生成一个随机整数。
```
RANDOMIZED-PARTITION(A, q, r)
	i = RANDOM(q, r)
	把A[i]和A[r]的值互换
	//下面的 PARTITION 函数是指 7.1中的PARTITION函数。
	return PARTITION(A, q, r)
```

```
//主调函数。
RANDOMIZED-QUICKSORT(A, p, r)
	if q < r
		q = PRANDOMIZED-ARTITION(A, q, r)
		RANDOMIZED-QUICKSORT(A, p, q-1)
		RANDOMIZED-QUICKSORT(A, p+1, r)
```