# Evaluate Reverse Polish Notation

[![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/evaluate-reverse-polish-notation/)

You are given an array of strings tokens that represents an arithmetic expression in a Reverse Polish Notation.

Evaluate the expression. Return an integer that represents the value of the expression.

### Example 1
```
Input: tokens = ["2","1","+","3","*"]
Output: 9
Explanation: ((2 + 1) * 3) = 9
```
### Example 2
```
Input: tokens = ["4","13","5","/","+"]
Output: 6
Explanation: (4 + (13 / 5)) = 6
```
### Example 3
```
Input: tokens = ["10","6","9","3","+","-11","*","/","*","17","+","5","+"]
Output: 22
Explanation: ((10 * (6 / ((9 + 3) * -11))) + 17) + 5
= ((10 * (6 / (12 * -11))) + 17) + 5
= ((10 * (6 / -132)) + 17) + 5
= ((10 * 0) + 17) + 5
= (0 + 17) + 5
= 17 + 5
= 22

```

### Solution
```java
class Solution {
    public int evalRPN(String[] tokens) {
        Stack<Integer> stack = new Stack<>() ;
        Set<String> o = new HashSet<>(Arrays.asList("+", "-", "*", "/")) ;
        for (String i:tokens) 
        {
            if(!o.contains(i)) 
                stack.push(Integer.valueOf(i));
            else 
            {
                int a = stack.pop(), b = stack.pop();
                if(i.equals("+")) 
                    stack.push(a + b);
                else if(i.equals("-")) 
                    stack.push(b - a);
                else if(i.equals("*")) 
                    stack.push(a*b);
                else 
                    stack.push(b/a);
            }
        }
        return stack.peek() ;
    }
}
```

### Accepted
[![image](https://user-images.githubusercontent.com/98543049/210163286-25ca407f-a20d-4408-9901-c7d3dd179d7d.png)
](https://leetcode.com/submissions/detail/868886687/)
