# Number of Substrings Containing All Three Characters

[![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/number-of-substrings-containing-all-three-characters/)



### Solution
```java
class Solution {
     public int numberOfSubstrings(String s) {
        int last[] = {-1, -1, -1}, res = 0, n = s.length();
        for (int i = 0; i < n; ++i) {
            last[s.charAt(i) - 'a'] = i;
            res += 1 + Math.min(last[0], Math.min(last[1], last[2]));
        }
        return res;
    }
}
```


### Accepted
[![image](https://user-images.githubusercontent.com/98543049/210805563-5fb12194-9232-4c14-bff3-0323e51aab3b.png)](https://leetcode.com/submissions/detail/871945612/)
