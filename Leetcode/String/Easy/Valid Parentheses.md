### Question:
https://leetcode.com/problems/valid-parentheses/

### Algo:
Stack

### Sol:
```
class Solution {
    public boolean isValid(String s) {
        
        Map<Character, Character> closeToOpen = new HashMap<>() {{
            put(')', '(');
            put('}', '{');
            put(']', '[');
        }};
        
        Stack<Character> stack = new Stack<>();
        
        for(int i = 0; i < s.length(); i++){
            char ch = s.charAt(i);
            Character open = closeToOpen.get(ch);
            if(open != null){
                if(stack.isEmpty() || stack.peek() != open)
                    return false;
                
                stack.pop();
            } else 
                stack.push(ch);
        }
        
        return stack.isEmpty();
    }
}
```
