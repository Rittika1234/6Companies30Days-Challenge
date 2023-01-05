# Minimum Deletions to Make Array Divisible

[![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/minimum-deletions-to-make-array-divisible/)



### Solution
```java
class Solution {
    public int minOperations(int[] nums, int[] numsDivide) {
       int gcd = findGCD(numsDivide);
        Arrays.sort(nums);
        for(int i=0; i< nums.length; i++){
            if(gcd % nums[i] == 0)
                return i;
           
        }
         return -1;
    }
    
    private int findGCD(int[] numsDivide){
        int gcd = numsDivide[0];
        
        for(int i=1; i<numsDivide.length;i++){
            int num = numsDivide[i];
            while(num > 0){
                int tmp = gcd % num;
                gcd = num;
                num = tmp;
            }
        }
        return gcd;
    }
}
```


### Accepted
[![image](https://user-images.githubusercontent.com/98543049/210804466-c42e880f-4c07-4d18-b2c0-4c5b03a54d23.png)](https://leetcode.com/submissions/detail/871970317/)
