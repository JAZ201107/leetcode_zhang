# 0098 Validate Binary Search Tree

[Question](https://leetcode.com/problems/validate-binary-search-tree/)

![](<../.gitbook/assets/image (1) (2) (1).png>)



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
    public boolean isValidBST(TreeNode root) {
        return checkNode(root, Long.MIN_VALUE, Long.MAX_VALUE);
    }
    
    public boolean checkNode(TreeNode node, long min, long max){
        if (node == null) return true;
        if (node.val > min 
            && node.val < max){
            return checkNode(node.left, min, node.val) && checkNode(node.right, node.val, max);
        }else{
                return false;
        }
    }
}
```
