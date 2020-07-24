For every node, length of longest path which pass it = MaxDepth of its left subtree + MaxDepth of its right subtree.
递归的方法，对于任何一个节点而言，最长的path等于左边的加右边的最大值
```java
public class Solution {
    int max = 0;
    
    public int diameterOfBinaryTree(TreeNode root) {
        maxDepth(root);
        return max;
    }
    
    private int maxDepth(TreeNode root) {
        if (root == null) return 0;
        
        int left = maxDepth(root.left);
        int right = maxDepth(root.right);
        
        max = Math.max(max, left + right);
        
        return Math.max(left, right) + 1;
    }
}
```
