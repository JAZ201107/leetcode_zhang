# 0090 Subsets II

[Question](https://leetcode.com/problems/subsets-ii/description/?envType=study-plan\&id=algorithm-ii)

<figure><img src="../.gitbook/assets/image (2) (2).png" alt=""><figcaption></figcaption></figure>

My Solution:

```java
class Solution {
    public List<List<Integer>> subsetsWithDup(int[] nums) {
        List<List<Integer>> list = new ArrayList<>();
        Arrays.sort(nums);
        helper(list, new ArrayList<>(), nums,0);
        return list;
    }


    private void helper(List<List<Integer>> list, List<Integer> tempList, int[] nums, int start){
        list.add(new ArrayList<>(tempList));
        for(int i = start; i < nums.length; i++){
            if(i>start
            && nums[i] == nums[i-1]){
                continue; // skip the duplicate
            }
            tempList.add(nums[i]);
            helper(list, tempList, nums, i+1);
            tempList.remove(tempList.size() - 1);
        }
    }
}
```
