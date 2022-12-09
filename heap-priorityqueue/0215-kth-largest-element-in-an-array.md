# 0215 Kth Largest Element in an Array

[Question ](https://leetcode.com/problems/kth-largest-element-in-an-array/description/)

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public int findKthLargest(int[] nums, int k) {
        PriorityQueue<Integer> maxHeap = new PriorityQueue<>((a,b) -> b-a);

        for (int x : nums)
        {
            maxHeap.offer(x);
        }

        for (int i = 0; i < k - 1; i++)
        {
            maxHeap.poll();
        }
        
        return maxHeap.peek();
    }
}
```
