# 0384 Shuffle an Array

[Question](https://leetcode.com/problems/shuffle-an-array/description/?envType=study-plan\&id=algorithm-ii)

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    int original [];

    public Solution(int[] nums) {
        this.original = nums.clone();
    }
    
    public int[] reset() {
        return this.original.clone();
    }
    
    public int[] shuffle() {
        int[] shuf = this.original.clone();
        Random random = new Random();
        for(int i = 0; i < shuf.length; i++){
            swap(shuf, i, i + random.nextInt(shuf.length - i));
        }
        return shuf;
    }


    private void swap(int[] arr, int a, int b){
        int temp = arr[a];
        arr[a] = arr[b];
        arr[b] = temp;
    }
}

/**
 * Your Solution object will be instantiated and called as such:
 * Solution obj = new Solution(nums);
 * int[] param_1 = obj.reset();
 * int[] param_2 = obj.shuffle();
 */
```
