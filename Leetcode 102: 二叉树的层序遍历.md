I use a queue to implement BFS. Each time when I poll a node, I add this node value to level. I use a variable zigzag to indicate whether add from left to right or right to left. If zigzag == false, it is from left to right; if zigzag == true, it is from right to left.
And from right to left just need to use ArrayList.add(0, value) method
```java
List<List<Integer>> res = new ArrayList<>();
if (root == null) return res;
Queue<TreeNode> queue = new LinkedList<>();
queue.add(root);
boolean zigzag = false;
while (!queue.isEmpty()) {
    List<Integer> level = new ArrayList<>();
    int cnt = queue.size();
    for (int i = 0; i < cnt; i++) {
        TreeNode node = queue.poll();
        if (zigzag) {
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
    zigzag = !zigzag;
}
return res;
```



