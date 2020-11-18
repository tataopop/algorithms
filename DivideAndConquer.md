# Divide and Conquer

### Leetcode 53 : Maximum Subarray

Given an integer array nums, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

Follow up: If you have figured out the O(n) solution, try coding another solution using the divide and conquer approach, which is more subtle.

 

#### Example 1:
```
Input: nums = [-2,1,-3,4,-1,2,1,-5,4]
Output: 6
Explanation: [4,-1,2,1] has the largest sum = 6.
```

#### Solution :
```
class Solution {
    public int maxSubArray(int[] nums) {
        return merge(nums, 0 ,nums.length - 1)[2];
    }
    
    // 0 : left max
    // 1 : right max
    // 2 : max sum
    // 3 : total sum
    public int[] merge(int[] nums, int l, int h) {
        if(l == h) return new int[]{nums[l], nums[l], nums[l], nums[l]};
        int mid = l + (h - l) / 2;
        int[] left = merge(nums, l, mid);
        int[] right = merge(nums, mid + 1, h);
        int[] res = new int[4];
        res[0] = Math.max(left[0], left[3] + right[0]);
        res[1] = Math.max(left[1] + right[3], right[1]);
        res[2] = Math.max(left[1] + right[0], Math.max(left[2], right[2]));
        res[3] = left[3] + right[3];
        return res;
    }
}
```
