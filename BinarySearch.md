# Binary Search
```
class Solution {
    public int search(int[] nums, int target) {
        int l = 0, h = nums.length - 1;
        while(l < h) {
            int m = l + (h - l) / 2;
            if(nums[m] < target) l = m + 1;
            else h = m;
        }
        return nums[l] == target ? l : -1;
    }
}
```
