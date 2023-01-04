# Largest Divisible Subset


[![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/largest-divisible-subset/)

Given a set of **distinct** positive integers nums, return the largest subset answer such that every pair (answer[i], answer[j]) of elements in this subset satisfies:

* answer[i] % answer[j] == 0, or
* answer[j] % answer[i] == 0

If there are multiple solutions, return any of them.

### Example 1
```
Input: nums = [1,2,3]
Output: [1,2]
Explanation: [1,3] is also accepted.
```
### Example 2
```
Input: nums = [1,2,4,8]
Output: [1,2,4,8]
```

### Solution
```java
class Solution {
    public List<Integer> largestDivisibleSubset(int[] nums) {
        List<Integer> res = new ArrayList<>();
        int n = nums.length,max = 0,prev = 0,idx=0;
        int dp[] = new int[n];
        
        Arrays.sort(nums);
        
        for(int i = 0;i<nums.length;i++){
            dp[i] = 1;
            for(int j=0;j<i;j++){
                if((nums[i] % nums[j] == 0) && (dp[j] >= dp[i])){
                    dp[i] = dp[j] + 1;
                }
            }
            if(dp[i] > max){
                max = dp[i];
                prev = nums[i];
                idx = i;
            }
        }
        
        for(int i = idx;i>=0;i--){
            if(max == 0)break;
            if(dp[i] == max && prev % nums[i] == 0){
                res.add(nums[i]);
                prev = nums[i];
                max--;
            }
        }
        
        return res;
    }
}
```

### Accepted
[![image](https://user-images.githubusercontent.com/98543049/210211333-71cd0c00-8a4f-4bd6-999e-73227cdafc00.png)](https://leetcode.com/submissions/detail/869569652/)
