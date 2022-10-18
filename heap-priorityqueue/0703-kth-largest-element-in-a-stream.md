# 0703 Kth Largest Element in a Stream

[Question](https://leetcode.com/problems/kth-largest-element-in-a-stream/)



![](<../.gitbook/assets/image (1) (1).png>)



```java
class KthLargest {

    private static int k;
    private PriorityQueue<Integer> heap;
    public KthLargest(int k, int[] nums) {
        this.k = k;
        heap = new PriorityQueue<>();
        
        for(int num: nums){
            heap.offer(num);
        }
        
        while(heap.size() > k){
            heap.poll(); // move the element before k'th
        }
    }
    
    public int add(int val) {
        heap.offer(val);
        if(heap.size() > k){
            heap.poll();
        }
        
        return heap.peek();
    }
}

/**
 * Your KthLargest object will be instantiated and called as such:
 * KthLargest obj = new KthLargest(k, nums);
 * int param_1 = obj.add(val);
 */
```