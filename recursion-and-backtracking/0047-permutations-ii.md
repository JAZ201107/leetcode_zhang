# 0047 Permutations II

[Question](https://leetcode.com/problems/permutations-ii/description/?envType=study-plan\&id=algorithm-ii)

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>



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



My Solution 2:

```java
class Solution {
    public List<List<Integer>> permuteUnique(int[] nums) {
        List<List<Integer>> res = new ArrayList<>();
        Arrays.sort(nums); 
        List<Integer> temp  = new ArrayList<>();
        boolean[] vis = new boolean[nums.length];
        helper(res, temp, nums, vis );
        
        return res;
    }

    private void helper(List<List<Integer>> res, List<Integer> temp, int[] nums, boolean[] vis){
        if(nums.length == temp.size()){
            res.add(new ArrayList<>(temp));
            return;
        }

        for(int i = 0; i < nums.length; i++){
            if(vis[i]){
                continue;
            }
            if(i > 0
            && !vis[i-1]
            && nums[i] == nums[i-1] ){
                continue; // duplicate
            }

            vis[i] = true;
            temp.add(nums[i]);

            helper(res, temp, nums, vis);
            temp.remove(temp.size() - 1);
            vis[i] = false;
        }
    }
}
```
