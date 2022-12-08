# 0173 Binary Search Tree Iterator

[Question](https://leetcode.com/problems/binary-search-tree-iterator/description/?envType=study-plan\&id=data-structure-ii)

<figure><img src="../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>

## JAVA

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
class BSTIterator {

    private Stack<TreeNode> stack = new Stack<TreeNode>();
    public BSTIterator(TreeNode root) {
        pushAllLeft(root);
    }

    private void pushAllLeft(TreeNode node){
        while (node != null){
            stack.push(node);
            node = node.left;
        }
    }
    
    public int next() {
        if (hasNext()){
            TreeNode tmpNode = stack.pop();
            pushAllLeft(tmpNode.right);
            return tmpNode.val;
        }else{
            return -1;
        }
    }
    
    public boolean hasNext() {
        return !stack.isEmpty();
    }
}

/**
 * Your BSTIterator object will be instantiated and called as such:
 * BSTIterator obj = new BSTIterator(root);
 * int param_1 = obj.next();
 * boolean param_2 = obj.hasNext();
 */
```

## Python

My Solution:

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class BSTIterator:

    def __init__(self, root: Optional[TreeNode]):
        self.arr = []
        self.pushAllLeft(root)
    
    def pushAllLeft(self, root):
        node = root
        while node is not None:
            self.arr.append(node)
            node = node.left
        
        

    def next(self) -> int:
        if not self.hasNext():
            return None
        smallest = self.arr.pop()
        self.pushAllLeft(smallest.right)
        return smallest.val
        

    def hasNext(self) -> bool:
        if len(self.arr) > 0:
            return True
        else:
            return False
    

        


# Your BSTIterator object will be instantiated and called as such:
# obj = BSTIterator(root)
# param_1 = obj.next()
# param_2 = obj.hasNext()
```



##

