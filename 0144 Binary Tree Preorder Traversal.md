[Question](https://leetcode.com/problems/binary-tree-preorder-traversal/)



<img src="0144 Binary Tree Preorder Traversal/image-20221012192707366.png">



My Solution:

```java
public List<Integer> preorderTraversal(TreeNode root) {
        List<Integer> list = new ArrayList<>();
        in(root, list);
        return list;
    }
    
    private void in(TreeNode root, List<Integer> list){
        if(root == null)
            return;
        list.add(root.val);
        in(root.left, list);
        in(root.right, list);
    }
```

