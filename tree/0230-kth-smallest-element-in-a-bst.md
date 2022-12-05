# 0230 Kth Smallest Element in a BST

[Question](https://leetcode.com/problems/kth-smallest-element-in-a-bst/)

<figure><img src="../.gitbook/assets/image (1) (2) (2) (1).png" alt=""><figcaption></figcaption></figure>



My Solution 1: Recursively

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    int count = 0;
    int result = Integer.MIN_VALUE;
    public int kthSmallest(TreeNode root, int k) {
        helper(root, k);
        return result;
    }
    
    
    private void helper(TreeNode root, int k){
        if(root == null){
            return;
        }
        helper(root.left, k);
        count++;
        if(count == k){
            result = root.val;
        }
        helper(root.right, k);
    }
}
```



## Python

My Solution 2: Iteratively

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def kthSmallest(self, root: Optional[TreeNode], k: int) -> int:
        n = 0
        stack = []
        cur = root

        while cur or stack:
            while cur:
                stack.append(cur)
                cur = cur.left
            
            cur = stack.pop()
            n += 1
            if n == k:
                return cur.val
            cur = cur.right

```
