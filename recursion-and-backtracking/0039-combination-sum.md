# 0039 Combination Sum

[Question](https://leetcode.com/problems/combination-sum/description/?envType=study-plan\&id=algorithm-ii)

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>



My Solution:

## Java

```java
class Solution {
    public List<List<Integer>> combinationSum(int[] candidates, int target) {
        Arrays.sort(candidates);
        List<List<Integer>> res = new ArrayList<>();
        if(target < candidates[0]){
            return res;
        }
        List<Integer> temp = new ArrayList<>();
        helper(res, temp, candidates, target, 0);
        return res;
    }

    private void helper(List<List<Integer>> res, List<Integer> temp, int [] candidates, int remain, int start){
        if(remain < 0) {
            return;
        }else if(remain == 0) {
            res.add(new ArrayList<>(temp));
        }else{ 
            for(int i = start; i < candidates.length; i++){
                temp.add(candidates[i]);
                helper(res, temp, candidates, remain - candidates[i], i);  
                temp.remove(temp.size() - 1);
            }
        }
    }
}
```





## Python

```python
class Solution:
    def combinationSum(self, candidates: List[int], target: int) -> List[List[int]]:
        res = []
        
        def dfs(i, cur, total):
            if total == target:
                res.append(cur.copy())
                return
            if i >= len(candidates) or total > target:
                return
            
            cur.append(candidates[i])
            dfs(i, cur, total + candidates[i])
            cur.pop()
            dfs(i+1, cur, total)

        dfs(0, [], 0)
        return res
```
