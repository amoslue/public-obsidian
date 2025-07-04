### how to sort array with index
		queries = sorted([(q, i) for i,q in enumerate(queries)])
		
#leetcode 
快排找Kth:
快排图解
![[Pasted image 20250701233316.png]]
```java
public class KthLargestQuickSort {

    public static int findKthLargest(int[] nums, int k) {
        int n = nums.length;
        k = n - k; // Convert to Kth smallest
        int low = 0, high = n - 1;
        
        while (low < high) {
            int pivotIndex = partition(nums, low, high);
            if (pivotIndex < k) {
                low = pivotIndex + 1;
            } else if (pivotIndex > k) {
                high = pivotIndex - 1;
            } else {
                break;
            }
        }
        
        return nums[k];
    }

    private static int partition(int[] nums, int low, int high) {
        int pivot = nums[high];
        int i = low;
        for (int j = low; j < high; j++) {
            if (nums[j] <= pivot) {
                swap(nums, i++, j);
            }
        }
        swap(nums, i, high);
        return i;
    }

    private static void swap(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }

    public static void main(String[] args) {
        int[] nums = {3, 2, 1, 5, 6, 4};
        int k = 2;
        System.out.println("The " + k + "th largest element is: " + findKthLargest(nums, k));
    }
}


```

[min sum of subarray](https://leetcode.cn/problems/sum-of-subarray-minimums/)

Java拷贝部分数组：
```
Arrays.copyOfRange(nums, 0, n);
```

（不包含右边界）

***

二分查找统一逻辑：
1. right = nums.length -1
2. while (left <= right)
3. 寻找边界
	1. 找左边界： 
	```java
		else if (nums[mid] == target) {
		 // 别返回，锁定左侧边界
		 right = mid - 1;
		}
		结束后判断是否越界：
		if (left == nums.length) return -1;
		return nums[left] == target ? left : -1;
	```	
	
	2. 找右边界：
	```java
			else if (nums[mid] == target) {
			 // 别返回，锁定右侧边界
			 left = mid + 1;
			}
			if (left == nums.length) return -1;
			return nums[left] == target ? left : -1;
	```
![[Pasted image 20250504181153.png]]

java堆：
![[Pasted image 20231031132319.png]]
Java PriorityQueue is ordered in **ascending order** by default. 
默认小顶堆，大顶堆写法：
```
maxHeap = new PriorityQueue<>((o1, o2) -> o2 - o1);
```

#leetcode [大小顶堆](https://leetcode.cn/problems/find-median-from-data-stream/description/?envType=study-plan-v2&envId=top-interview-150)


