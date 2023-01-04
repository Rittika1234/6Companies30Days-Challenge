# Longest Happy Prefix

[![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/longest-happy-prefix/)



### Solution
```java
class Solution {
    public String longestPrefix(String s) {
        int j=0;
        int i=1;
        int prefix[]=new int[s.length()];
        while(i<s.length()){
            if(s.charAt(i)==s.charAt(j)){
                prefix[i]=j+1;
                i++;
                j++;
            }
            else{
                if(j==0){
                    prefix[i]=0;
                    i++;
                }
                else{
                    j=prefix[j-1];
                }
            }
        }
        return s.substring(0,prefix[s.length()-1]);
    }
}
```

### Accepted
[![image](https://user-images.githubusercontent.com/98543049/210519601-f4334f9c-fe10-4056-be06-c13ab781e289.png)](https://leetcode.com/submissions/detail/871067518/)

