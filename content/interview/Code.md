1. 二分
2. LRU 
3. java堆：
![[Pasted image 20231031132319.png]]
Java PriorityQueue is ordered in **ascending order** by default. 
默认小顶堆，大顶堆写法：
```
maxHeap = new PriorityQueue<>((o1, o2) -> o2 - o1);
```

#leetcode [大小顶堆](https://leetcode.cn/problems/find-median-from-data-stream/description/?envType=study-plan-v2&envId=top-interview-150)


