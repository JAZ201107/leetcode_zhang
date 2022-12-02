# 0040 Combination Sum II

[Question](https://leetcode.com/problems/combination-sum-ii/description/?envType=study-plan\&id=algorithm-ii)

<figure><img src="../.gitbook/assets/image (2) (1) (5).png" alt=""><figcaption></figcaption></figure>



My Solution:

## Java

```java
class Solution {
    public List<List<Integer>> combinationSum2(int[] candidates, int target) {
        List<List<Integer>> list = new LinkedList<List<Integer>>();
        Arrays.sort(candidates);
        backtrack(list, new ArrayList<Integer>(), candidates, target, 0);
        return list;
    }

        private void backtrack(List<List<Integer>> list, List<Integer> tempList, int[] cand, int remain, int start){
        
        if(remain < 0){
            return; 
        }else if(remain == 0){
        list.add(new ArrayList<>(tempList));
        }else{
            for (int i = start; i < cand.length; i++) {
                if(i > start && cand[i] == cand[i-1]) {
                    continue; 
                }
                tempList.add(cand[i]);
                backtrack(list, tempList, cand, remain - cand[i], i+1);
                tempList.remove(tempList.size() - 1);
            }
        }
    }
}
```



## Python

```python
class Solution:
    def combinationSum2(self, candidates: List[int], target: int) -> List[List[int]]:
        candidates.sort()

        res = []

        def helper(cur, pos, target):
            if target == 0:
                res.append(cur.copy())
                return
            if target <= 0:
                return
            
            prev = -1
            for i in range(pos, len(candidates)):
                if candidates[i] == prev:
                    continue
                cur.append(candidates[i])
                helper(cur, i + 1, target - candidates[i])
                cur.pop()
                prev = candidates[i]
        helper([], 0, target)
        return res
```
