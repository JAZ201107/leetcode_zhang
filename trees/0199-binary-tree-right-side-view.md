# 0199 Binary Tree Right Side View

[Question](https://leetcode.com/problems/binary-tree-right-side-view/)

![](<../.gitbook/assets/image (1).png>)

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
    public List<Integer> rightSideView(TreeNode root) {
        List<Integer> res = new ArrayList<>();
        from_right(root, res, 0);
        return res;
    }

    
    private void from_right(TreeNode root, List<Integer> res, int depth){
        if(root == null){
            return;
        }
        
        if(depth == res.size()){
            res.add(root.val);
        }
        
        from_right(root.right, res, depth+1);
        from_right(root.left, res, depth+1);
        
    }
}
```
