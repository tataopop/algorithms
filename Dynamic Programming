# Dynamic Programming

### Leetcode 312. Burst Balloons

You are given n balloons, indexed from 0 to n - 1. Each balloon is painted with a number on it represented by an array nums. You are asked to burst all the balloons.

If you burst the ith balloon, you will get nums[i - 1] * nums[i] * nums[i + 1] coins. If i - 1 or i + 1 goes out of bounds of the array, then treat it as if there is a balloon with a 1 painted on it.

Return the maximum coins you can collect by bursting the balloons wisely.

#### Example :
```
Input: nums = [3,1,5,8]
Output: 167
Explanation:
nums = [3,1,5,8] --> [3,5,8] --> [3,8] --> [8] --> []
coins =  3*1*5    +   3*5*8   +  1*3*8  + 1*8*1 = 167
```

#### Solution :
```
class Solution {
    public int maxCoins(int[] input) {
        int n = input.length + 2;
        int[] nums = new int[n];
        nums[0] = nums[n - 1] = 1;
        for(int i = 1; i < n - 1; i++) {
            nums[i] = input[i - 1];
        }
        int[][] dp = new int[n][n];
        for(int k = 2; k < n; k++) {
            for(int left = 0; left + k < n; left++) {
                int right = left + k;
                dp[left][right] = 0;
                for(int i = left + 1; i < right; i++) {
                    dp[left][right] = Math.max(dp[left][right], dp[left][i] + dp[i][right] + nums[left] * nums[i] * nums[right]);
                }
            }
        }
        return dp[0][n - 1];
    }
}
```
