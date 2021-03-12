# Binary Search Tree 


### Leetcode 1373. Maximum Sum BST in Binary Tree

Given a binary tree root, the task is to return the maximum sum of all keys of any sub-tree which is also a Binary Search Tree (BST).

Assume a BST is defined as follows:

The left subtree of a node contains only nodes with keys less than the node's key.
The right subtree of a node contains only nodes with keys greater than the node's key.
Both the left and right subtrees must also be binary search trees.

#### Example 1:
```
Input: root = [1,4,3,2,4,2,5,null,null,null,null,null,null,4,6]
Output: 20
Explanation: Maximum sum in a valid Binary search tree is obtained in root node with key equal to 3.
```

#### Solution : 
```
class Solution {
    int max;
    public int maxSumBST(TreeNode root) {
        max = 0;
        findMaxSum(root);
        return max;
    }
    
    //int[]{isBST(0/1), largest, smallest, sum}
    public int[] findMaxSum(TreeNode node){
        if(node==null){
            return new int[]{1, Integer.MIN_VALUE, Integer.MAX_VALUE, 0};
        }
        int[] left = findMaxSum(node.left);
        int[] right = findMaxSum(node.right);
        boolean isBST = left[0]==1 && right[0]==1 && node.val>left[1] && node.val<right[2];
        int sum = node.val + left[3] + right[3];
        if(isBST){
            max = Math.max(max, sum);
        }
        return new int[]{isBST?1:0, Math.max(node.val,right[1]), Math.min(node.val,left[2]), sum};
    }
}
```
