使用一个队列来实现广度优先搜索。每当移除一个节点，将这个节点加入到这一层中
If z == false, it is from left to right; if z == true, it is from right to left.
And from right to left just need to use ArrayList.add(0, value) method
```java
List<List<Integer>> res = new ArrayList<>();
if (root == null) return res;
Queue<TreeNode> queue = new LinkedList<>();
queue.add(root);
boolean z = false;
while (!queue.isEmpty()) {
    List<Integer> level = new ArrayList<>();
    int cnt = queue.size();
    for (int i = 0; i < cnt; i++) {
        TreeNode node = queue.poll();
        if (z) {
            level.add(0, node.val);
        }
        else {
            level.add(node.val);
        }
        if (node.left != null) {
            queue.add(node.left);
        }
        if (node.right != null) {
            queue.add(node.right);
        }
    }
    res.add(level);
    z = !z;
}
return res;
```



