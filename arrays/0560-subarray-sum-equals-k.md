# 0560 Subarray Sum Equals K

[Question](https://leetcode.com/problems/subarray-sum-equals-k/description/)

<figure><img src="../.gitbook/assets/image (1) (5).png" alt=""><figcaption></figcaption></figure>

My Solution: Brute Force

```java
class Solution {
    public int subarraySum(int[] nums, int k) {
        int counter = 0;
        for(int i = 0; i < nums.length; i++){
            int sum = 0;
            for(int j = i; j < nums.length; j++){
                sum += nums[j];
                if(sum == k){
                    counter++;
                }
            }
        }
        return counter;
    }
}
```



My Solution 2:

```java
class Solution {
    public int subarraySum(int[] nums, int k) {
        Map<Integer, Integer> sums = new HashMap<>();
        sums.put(0,1);

        int sum = 0;
        int count = 0;

        for(int i : nums){
            sum += i;
            count += sums.getOrDefault(sum - k, 0);
            sums.merge(sum, 1, (v1, v2) -> v1 + v2);
        }

        return count;
    }
}
```
