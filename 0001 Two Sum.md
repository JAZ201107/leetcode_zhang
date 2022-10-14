[Question](https://leetcode.com/problems/two-sum/)

<img src="0001 Two Sum/image-20221013210618151.png">



My Solution:

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        // elements are key, index are value
        HashMap<Integer, Integer> indexMap = new HashMap<>();
        for(int i = 0; i < nums.length; i++){
            if(indexMap.containsKey(target - nums[i]))
                return new int[]{indexMap.get(target - nums[i]), i};
            
            indexMap.put(nums[i], i);
        }
        return null;
    }
}
```

