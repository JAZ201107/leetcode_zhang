# 0239 Sliding Window Maximum

Question

<figure><img src="../.gitbook/assets/image (30).png" alt=""><figcaption></figcaption></figure>



My Solution:

```python
class Solution:
    def maxSlidingWindow(self, nums: List[int], k: int) -> List[int]:
        output = []
        q = collections.deque() # index
        l, r = 0, 0

        while r < len(nums):
            # pop smaller values from q
            while q and nums[q[-1]] < nums[r]:
                q.pop()
            q.append(r)
        
            # remove left val from window
            if l > q[0]:
                q.popleft()
            
            if (r + 1) >= k:
                output.append(nums[q[0]])
                l += 1
            r += 1
        return output
```
