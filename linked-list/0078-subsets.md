# 0078 Subsets

[Question](https://leetcode.com/problems/subsets/?envType=study-plan\&id=algorithm-ii)

<figure><img src="../.gitbook/assets/image (3) (1) (1).png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>> list = new ArrayList<>();
        Arrays.sort(nums);
        helper(list,new ArrayList<>(), nums, 0);
        return list;
    }


    private void helper(List<List<Integer>> list, List<Integer> tempList, int[] nums, int start){
        list.add(new ArrayList<>(tempList));
        for(int i = start; i < nums.length; i++){
            tempList.add(nums[i]);
            helper(list, tempList, nums, i+1);
            tempList.remove(tempList.size() - 1); // remove last element
        }
    }
}
```
