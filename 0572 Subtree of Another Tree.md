[Question](https://leetcode.com/problems/subtree-of-another-tree/)



<img src="0572 Subtree of Another Tree/image-20221014144451524.png">



My Solution:

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
    public boolean isSubtree(TreeNode root, TreeNode subRoot) {
        if (root == null) 
            return false;
        if (dfs(root, subRoot)) 
            return true;
        return isSubtree(root.left, subRoot) || isSubtree(root.right, subRoot);
    }

    public boolean dfs(TreeNode root, TreeNode subRoot) {
        if (root == null && subRoot == null) 
            return true;
        if (root == null || subRoot == null) 
            return false;
        if (root.val != subRoot.val) 
            return false;
        return dfs(root.left, subRoot.left) && dfs(root.right, subRoot.right);
    }
}
```

