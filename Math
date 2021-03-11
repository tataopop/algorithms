# Math

### Leetcode 43. Multiply Strings

Given two non-negative integers num1 and num2 represented as strings, return the product of num1 and num2, also represented as a string.

#### Example :
```
Input: num1 = "123", num2 = "456"
Output: "56088"
```

#### Solution :
```
class Solution {
    public String multiply(String num1, String num2) {
        int m = num1.length(), n = num2.length();
        int[] pos = new int[m + n];
        for(int i = m - 1; i >= 0; i--) {
            for(int j = n - 1; j >= 0; j--) {
                int mul = (num1.charAt(i) - '0') * (num2.charAt(j) - '0');
                int p1 = i + j, p2 = i + j + 1;
                int sum = pos[p2] + mul;
                pos[p1] += sum / 10;
                pos[p2] = sum % 10;
            }
        }
        StringBuilder sb = new StringBuilder();
        for(int i : pos) {
            if(sb.length() == 0 && i == 0) continue;
            sb.append(i);
        }
        return sb.length() == 0 ? "0" : sb.toString();
    }
}
```
