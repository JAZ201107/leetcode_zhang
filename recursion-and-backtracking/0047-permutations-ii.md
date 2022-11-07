# 0047 Permutations II

[Question](https://leetcode.com/problems/permutations-ii/description/?envType=study-plan\&id=algorithm-ii)

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public List<List<Integer>> permuteUnique(int[] nums) {
        List<List<Integer>> res = new ArrayList<>();
        helper(res, nums, 0);
        return res;
    }


    private void helper(List<List<Integer>> res, int[] nums, int index){
        if(index == nums.length){
            List<Integer> list = new ArrayList<>();
            for(int i = 0; i < nums.length; i++){
                list.add(Integer.valueOf(nums[i]));
            }
            res.add(list);
            return;
        }

        Set<Integer> set = new HashSet<>();
        for(int i = index; i < nums.length; i++){
            if(set.add(nums[i])){
                swap(nums, i , index);
                helper(res, nums, index+1);
                swap(nums, i , index);
            }
        }
    }


    private void swap(int[] nums, int i, int j){
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
}
```
