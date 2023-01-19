# 0416 Partition Equal Subset Sum

Question

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>



My Solution

```python
class Solution:
    def canPartition(self, nums: List[int]) -> bool:
        if sum(nums) % 2:
            return False
        
        dp = set()
        dp.add(0) # no element added
        target = sum(nums) // 2

        for i in range(len(nums) - 1, -1, -1): # backtrack
            nextDP = set()
            for t in dp:
                if (t + nums[i] == target):
                    return True # find the target
                
                nextDP.add(t + nums[i]) # not find target, add value to set
                nextDP.add(t) 
            dp = nextDP

        return True if target in dp else False
```
