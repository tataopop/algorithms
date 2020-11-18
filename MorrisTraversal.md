## Morris Traversal

Morris (InOrder) traversal is a tree traversal algorithm that does not employ the use of recursion or a stack

```
private void inorder(TreeNode root) {
   TreeNode node = root;
    while (node != null) {
        if (node.left == null) {
            //handleValue(node.val);
            node = node.right;
        } else {
            TreeNode prev = node.left;
            while (prev.right != null && prev.right != node)
                prev = prev.right;
            if (prev.right == null) {
                prev.right = node;
                node = node.left;
            } else {
                prev.right = null;
                //handleValue(node.val);
                node = node.right;
            }
        }
    }
}
```
