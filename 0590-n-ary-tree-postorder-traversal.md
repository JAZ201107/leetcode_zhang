# 0590 N-ary Tree Postorder Traversal

[Question](https://leetcode.com/problems/n-ary-tree-postorder-traversal/)

![](.gitbook/assets/image-20221013013604586.png)

My Solution

```java
class Solution {
    List<Integer> res = new ArrayList<>();
    public List<Integer> postorder(Node root) {
        in(root);
        return res;
    }
    
    private void in(Node root){
        if (root == null)
            return;
        for (Node n: root.children){
            in(n);
        }
        res.add(root.val);
        
    }
}
```
