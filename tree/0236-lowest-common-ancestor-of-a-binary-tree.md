# 0236 Lowest Common Ancestor of a Binary Tree

[Question](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/description/?envType=study-plan\&id=data-structure-ii)

<figure><img src="../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>



My Solution:

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
        if(root.val == p.val || root.val == q.val){
            return root;
        }
        if(root.right == null && root.left == null){
            return null;
        }

        TreeNode left = null;
        TreeNode right = null;
        if(root.left != null){
            left = lowestCommonAncestor(root.left, p, q);
        }
        if(root.right != null){
            right = lowestCommonAncestor(root.right, p, q);
        }
        if(left != null && right != null){
            return root;
        }
        
        return left == null ? right : left;
        
    }
}
```
