# 0287 Find the Duplicate Number

Question

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>



My Solution:

```python
class Solution:
    def findDuplicate(self, nums: List[int]) -> int:
        # LinkedList problem
        # Floyd's Algorithms
        slow, fast = 0, 0
        while True:
            slow = nums[slow]
            fast = nums[nums[fast]]
            if slow == fast:
                break
            
        slow2 = 0
        while True:
            slow = nums[slow]
            slow2 = nums[slow2]
            if slow == slow2:
                return slow
```
