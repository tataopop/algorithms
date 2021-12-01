# Rolling hash

### Leetcode 1316: Distinct Echo Substrings

Return the number of distinct non-empty substrings of text that can be written as the concatenation of some string with itself 

(i.e. it can be written as a + a where a is some string).

#### Example :
```
Input: text = "abcabcabc"
Output: 3
Explanation: The 3 substrings are "abcabc", "bcabca" and "cabcab".
```

#### Solution :
```
class Solution {
    long BASE = 29L, MOD = 1000000007L;
    public int distinctEchoSubstrings(String text) {
        Set<Long> set = new HashSet<>();
        int n = text.length();
        long[] hash = new long[n + 1];
        long[] pow = new long[n + 1];
        pow[0] = 1;
        for(int i = 1; i <= n; i++) {
            hash[i] = (hash[i - 1] * BASE + text.charAt(i - 1)) % MOD;
            pow[i] = pow[i - 1] * BASE % MOD; 
        }
        for(int i = 0; i < n; i++) {
            for(int len = 1; i + len * 2 <= n; len++) {
                long hash1 = getHash(i, i + len, hash, pow);
                long hash2 = getHash(i + len, i + 2 * len, hash, pow);
                if(hash1 == hash2) set.add(hash1);
            }
        }
        return set.size();
    }
    
    /* explain : for 2354
        left : 23
        right : 2354
        the hash is 2354 - 23 * 100 = 54
    */
    long getHash(int l, int r, long[] hash, long[] pow) {
        return (hash[r] - hash[l] * pow[r -l] % MOD + MOD) % MOD;
    }
}
```
