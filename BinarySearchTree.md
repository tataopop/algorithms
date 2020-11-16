## Leetcode 315 : Count of Smaller Numbers After Self
You are given an integer array nums and you have to return a new counts array. The counts array has the property where `counts[i]` is the number of smaller elements to the right of nums[i].

### Example 1:
```
Input: nums = [5,2,6,1]
Output: [2,1,1,0]
```

### Solution : 
```
class Solution {
    public List<Integer> countSmaller(int[] nums) {
        Node root = null;
        Integer[] res = new Integer[nums.length];
        for(int i = nums.length - 1; i >= 0; i--) {
            root = insert(nums[i], root, res, i, 0);
        }
        return Arrays.asList(res);
    }
    
    private Node insert(int v, Node node, Integer[] res, int i, int preSum) {
        if(node == null) {
            node = new Node(v, 0);
            res[i] = preSum;
        } else if(v == node.val){
            node.dup++;
            res[i] = preSum + node.sum;
        } else if(v > node.val) {
            node.right = insert(v, node.right, res, i, preSum + node.sum + node.dup);
        } else {
            node.sum++;
            node.left = insert(v, node.left, res, i, preSum);
        }
        return node;
    }
    
    class Node {
        Node left, right;
        int val, sum, dup = 1;
        public Node(int v, int s) {
            this.val = v;
            this.sum = s;
        }
    }
}
```
