### Question:
https://leetcode.com/problems/basic-calculator-ii/

### Algo:
String, Math, Stack

### Sol (With stack):
```
class Solution {
    
    public int calculate(String s) {
        
        Stack<Integer> stack = new Stack<>();
        char sign = '+';
        
        for(int i = 0; i < s.length(); i++) {
            char ch = s.charAt(i);
            if(Character.isDigit(ch)) {
                int val = 0;
                
                while(i < s.length() && Character.isDigit(s.charAt(i))) {
                    val = val * 10 + (s.charAt(i) - '0');
                    i++;
                }
                
                i--;
                
                if(sign == '+') {
                    stack.push(val);
                }else if(sign == '-') {
                    stack.push(-val);
                }else if(sign == '*') {
                    stack.push(stack.pop() * val);
                }else if(sign == '/') {
                    stack.push(stack.pop()/val);
                }
                
            } else if(ch != ' ') {
                sign = ch;
            }
        }
        
        int sum = 0;
        
        while(!stack.isEmpty())
            sum += stack.pop();
        
        return sum;
    }
}
```

### Sol(Without Stack)
```
class Solution {
    
    public int calculate(String s) {
        
        int result, lastNumber, currentNumber;
        
        result = lastNumber = currentNumber = 0;
        char sign = '+';
        
        for(int i = 0; i < s.length(); i++) {
            char ch = s.charAt(i);
            if(Character.isDigit(ch)) {
                
                while(i < s.length() && Character.isDigit(s.charAt(i))) {
                    currentNumber = currentNumber * 10 + (s.charAt(i) - '0');
                    i++;
                }
                
                i--;
                
                if(sign == '+') {
                    result += lastNumber;
                    lastNumber = currentNumber;
                }else if(sign == '-') {
                    result += lastNumber;
                    lastNumber = -currentNumber;
                }else if(sign == '*') {
                    lastNumber = lastNumber * currentNumber;
                }else if(sign == '/') {
                    lastNumber = lastNumber/currentNumber;
                }
                
                currentNumber = 0;
                
            } else if(ch != ' ') {
                sign = ch;
            }
        }
        
        return result + lastNumber;
    }
}
```
