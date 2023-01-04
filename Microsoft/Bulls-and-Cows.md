# Bulls and Cows

[![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/bulls-and-cows/)

You are playing the **Bulls and Cows** game with your friend.

You write down a secret number and ask your friend to guess what the number is. When your friend makes a guess, you provide a hint with the following info:

* The number of "bulls", which are digits in the guess that are in the correct position.
* The number of "cows", which are digits in the guess that are in your secret number but are located in the wrong position. Specifically, the non-bull digits in the guess that could be rearranged such that they become bulls.
Given the secret number secret and your friend's guess guess, return the hint for your friend's guess.

The hint should be formatted as "xAyB", where x is the number of bulls and y is the number of cows. Note that both secret and guess may contain duplicate digits.

### Example 1
```
Input: secret = "1807", guess = "7810"
Output: "1A3B"
Explanation: Bulls are connected with a '|' and cows are underlined:
"1807"
  |
"7810"
```

### Example 2
```
Input: secret = "1123", guess = "0111"
Output: "1A1B"
Explanation: Bulls are connected with a '|' and cows are underlined:
"1123"        "1123"
  |      or     |
"0111"        "0111"
Note that only one of the two unmatched 1s is counted as a cow since the non-bull digits can only be rearranged to allow one 1 to be a bull.
```

### Solution
```java
class Solution {
    public String getHint(String secret, String guess) {
        int bulls=0, cows =0;
        int[] numbers = new int[10];
        for(int i=0; i<secret.length();i++){
            int s = secret.charAt(i)-'0';
            int g = guess.charAt(i)-'0';
            if(s == g)
                bulls++;
            else{
                if(numbers[s]++ < 0) cows++;
                if(numbers[g]-- > 0) cows++;
            }
        }
        return bulls + "A" + cows + "B";
    }
}
```

### Accepted
[![image](https://user-images.githubusercontent.com/98543049/210171579-e722fc57-5180-4bc0-9298-2024b463bb6b.png)](https://leetcode.com/submissions/detail/869059671/)
