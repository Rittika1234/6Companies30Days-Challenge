# Shortest Unsorted Continuous Subarray

[![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/shortest-unsorted-continuous-subarray/)



### Solution
```java
class Solution {
    public int findUnsortedSubarray(int[] nums) {
        int [] snums = nums.clone();
        Arrays.sort(snums);
        int start = snums.length, end=0;
        for(int i = 0; i< snums.length; i++){
            if(snums[i] != nums[i]){
                start = Math.min(start,i);
                end = Math.max(end, i);
            }
        }
        return (end - start >= 0 ? end - start +1 : 0);
    }
}
```

### Accepted
[![image](https://user-images.githubusercontent.com/98543049/210515201-c7853d46-e93b-481b-897e-546182202f22.png)
](https://leetcode.com/submissions/detail/871053354/)
