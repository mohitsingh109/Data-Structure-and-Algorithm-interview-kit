### Question:
https://leetcode.com/problems/longest-valid-parentheses/

### Algo:
Stack, String

### Sol:
```
class Solution {
    public int longestValidParentheses(String s) {
        
        int len = s.length();
        int start = 0;
        Stack<Integer> stack = new Stack<>();
        int size = 0;
        
        stack.push(-1);
        
        while(start < len) {
            if(s.charAt(start) == '(')
                stack.push(start);
            
            else {
                // pop item 
                stack.pop();
                
                //if stack is not empty take max of (current size) and (diff of stack peek and current index)
                if(!stack.isEmpty())
                    size = Math.max(size, start - stack.peek());
                else // if stack is empty push current index as base for next valid string
                    stack.push(start);
            }
            
            start++;
        }
        
        return size;
    }
}
```
