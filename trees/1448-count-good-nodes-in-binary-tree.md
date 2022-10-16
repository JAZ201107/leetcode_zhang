# 1448 Count Good Nodes in Binary Tree

[Question](https://leetcode.com/problems/count-good-nodes-in-binary-tree/)

![](../.gitbook/assets/image.png)

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

    int goodCount;
    public int goodNodes(TreeNode root) {
        goodCount = 0;
        cal(root, Integer.MIN_VALUE);
        return goodCount;
    }
    
    private void cal(TreeNode root, int max){
        if(root == null) 
            return;
        if(root.val >= max) 
            goodCount++;
        max = Math.max(max, root.val);
        cal(root.left, max);
        cal(root.right, max);
    }
    
}
```
