# SlidingWindow

### Leetcode 76. Minimum Window Substring

Given two strings s and t, return the minimum window in s which will contain all the characters in t. If there is no such window in s that covers all characters in t, return the empty string "".

Note that If there is such a window, it is guaranteed that there will always be only one unique minimum window in s.

#### Example :
```
Input: s = "ADOBECODEBANC", t = "ABC"
Output: "BANC"
```

#### Solution :
```
class Solution {
    public String minWindow(String s, String t) {
        int total = t.length(), i = 0, j = 0, len = Integer.MAX_VALUE, head = 0;
        int[] count = new int[128];
        for(char c : t.toCharArray()) {
            count[c]++;
        }
        while(j < s.length()) {
            if(count[s.charAt(j++)]-- > 0) total--;
            while(total == 0) {
                if(len > j - i) {
                    len = j - i;
                    head = i;
                }
                if(count[s.charAt(i++)]++ == 0) total++;
            }
        }
        return len > s.length() ? "" : s.substring(head, head + len);
    }
}
```
