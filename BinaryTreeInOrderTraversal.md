## Using stack
```
Stack<TreeNode> stack = new Stack<>();
while(root != null || !stack.isEmpty()) {
    while(root != null) {
        stack.push(root);
        root = root.left;
    }
    TreeNode cur = stack.pop();
    // add treatment
    root = cur.right;
}
```
## Using recursion
```
public void inorder(TreeNode node) {
    if(node == null) return;
    inorder(node.left);
    // add treatment
    inorder(node.right);
}
```

we can keep the previours node if needed :
```
TreeNode prev = null;
public void inorder(TreeNode node) {
    if(node == null) return;
    inorder(node.left);
    if(prev != null) 
      // add treatment
    prev = node;
    inorder(node.right);
}
```

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
