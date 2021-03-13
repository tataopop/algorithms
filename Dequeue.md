# Dequeue

### Leetcode 239. Sliding Window Maximum

You are given an array of integers nums, there is a sliding window of size k which is moving from the very left of the array to the very right. 
You can only see the k numbers in the window. Each time the sliding window moves right by one position.

Return the max sliding window.

#### Example :
```
Input: nums = [1,3,-1,-3,5,3,6,7], k = 3
Output: [3,3,5,5,6,7]
Explanation: 
Window position                Max
---------------               -----
[1  3  -1] -3  5  3  6  7       3
 1 [3  -1  -3] 5  3  6  7       3
 1  3 [-1  -3  5] 3  6  7       5
 1  3  -1 [-3  5  3] 6  7       5
 1  3  -1  -3 [5  3  6] 7       6
 1  3  -1  -3  5 [3  6  7]      7
```

#### Solution :
```
class Solution {
    public int[] maxSlidingWindow(int[] nums, int k) {
        int n = nums.length;
        int[] res = new int[n + 1 - k];
        Deque<Integer> q = new ArrayDeque<>();
        for(int i = 0; i < nums.length; i++) {
            while(!q.isEmpty() && q.peek() < i - k + 1) q.poll();
            while(!q.isEmpty() && nums[q.peekLast()] <= nums[i]) q.pollLast();
            q.offer(i);
            if(i >= k - 1) res[i - k + 1] = nums[q.peek()];
        }
        return res;
    }
}
```
