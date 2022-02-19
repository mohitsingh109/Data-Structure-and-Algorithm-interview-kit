### Question:
https://leetcode.com/problems/remove-k-digits/

### Algo:
String

### Sol:
```
class Solution {
   
    public String removeKdigits(String num, int k) {
        Stack<Integer> stack = new Stack<>();
        StringBuilder sb = new StringBuilder();
        
        for(int i = 0; i < num.length(); i++) {
            
            int value = num.charAt(i) - '0';
            
            while(!stack.isEmpty() && k > 0 && stack.peek() > value) {
                k--;
                stack.pop();
            }
            
            stack.push(value);
        }
        
        while(!stack.isEmpty()) {
            int value = stack.pop();
            if(k > 0)
                k--;
            else sb.append(value);
        }
        
        sb.reverse();
        
        while(sb.length() > 1 && sb.charAt(0) =='0')
            sb.deleteCharAt(0);
        
        return sb.length() == 0 ? "0" : sb.toString();
    }

}
```
