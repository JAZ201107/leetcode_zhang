# 0235 Lowest Common Ancestor of a Binary Search Tree

[Question](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/)

![](<../.gitbook/assets/image (1).png>)

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */

class Solution {
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        while(root != null) {
            if (p.val < root.val && q.val < root.val) {
                root = root.left; //Search left subtree
            } else if (p.val > root.val && q.val > root.val) {
                root = root.right; //search right
            } else {
                return root;
            }
        }
        
        return null;
    }
}
```
