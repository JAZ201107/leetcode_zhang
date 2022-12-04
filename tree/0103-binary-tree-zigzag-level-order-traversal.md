# 0103 Binary Tree Zigzag Level Order Traversal

[Question](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/description/?envType=study-plan\&id=data-structure-ii)

<figure><img src="../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>



My Solution:

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def zigzagLevelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
        output = []

        def dfs(node, level, output):
            if not node:
                return 
            
            if len(output) <= level:
                output += [[]]
            
            dfs(node.left, level + 1, output)
            dfs(node.right, level + 1, output)
            if level % 2 == 0:
                output[level].append(node.val)
            else:
                output[level].insert(0, node.val)
        
        dfs(root, 0, output)
        return output
```
