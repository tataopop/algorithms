# Backtracking

### Leetcode 39: Combination Sum

Given an array of distinct integers candidates and a target integer target, return a list of all unique combinations of candidates where the chosen numbers sum to target. You may return the combinations in any order.

The same number may be chosen from candidates an unlimited number of times. Two combinations are unique if the frequency of at least one of the chosen numbers is different.

It is guaranteed that the number of unique combinations that sum up to target is less than 150 combinations for the given input.

#### Example :
```
Input: candidates = [2,3,6,7], target = 7
Output: [[2,2,3],[7]]
Explanation:
2 and 3 are candidates, and 2 + 2 + 3 = 7. Note that 2 can be used multiple times.
7 is a candidate, and 7 = 7.
These are the only two combinations.
```

#### Solution :
```
class Solution {
    public List<List<Integer>> combinationSum(int[] candidates, int target) {
        List<List<Integer>> res = new ArrayList<>();
        helper(res, new ArrayList<>(), target, 0, candidates);
        return res;
    }

    public void helper(List<List<Integer>> res, List<Integer> list, int remain, int idx, int[] candidates) {
        if(remain < 0) return;
        if(remain == 0) {
            res.add(new ArrayList<>(list));
            return;
        }
        for(int i = idx; i < candidates.length; i++) {
            list.add(candidates[i]);
            helper(res, list, remain - candidates[i], i, candidates);
            list.remove(list.size() - 1);
        }
    }
}
```

### complexity
* n-queen problem:O(n!)

* graph coloring problem:O(nm^n)//where n=no. of vertex,m=no. of color used

* hamilton cycle:O(N!)

* WordBreak and StringSegment:O(2^N)

* subset sum problem:O(nW)
