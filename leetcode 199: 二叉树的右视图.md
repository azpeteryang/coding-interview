The core idea of this algorithm:

1.Each depth of the tree only select one node.
2. View depth is current size of result list.

Here is the code:
```java
public class Solution {
    public List<Integer> rightSideView(TreeNode root) {
        List<Integer> result = new ArrayList<Integer>();
        rightView(root, result, 0);
        return result;
    }
    
    public void rightView(TreeNode curr, List<Integer> result, int currDepth){
        if(curr == null){
            return;
        }
        if(currDepth == result.size()){                   //确保那一层的第一个元素会被加入到result里面
            result.add(curr.val);
        }
        
        rightView(curr.right, result, currDepth + 1);      //先右后左,返回rightview，先左后右，返回leftview
        rightView(curr.left, result, currDepth + 1);
        
    }
}
```
