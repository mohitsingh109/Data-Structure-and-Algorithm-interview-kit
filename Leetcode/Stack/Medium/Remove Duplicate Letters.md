### Question:
https://leetcode.com/problems/remove-duplicate-letters/

### Algo:
Monotonic Stack, Greedy, Bit-Masking

### Sol:
```
class Solution {
    public String removeDuplicateLetters(String s) {
        int len  = s.length();
        int usedChar = 0;
        
        int[] freq = new int[26];
        Stack<Character> stack = new Stack<>();
        
        for(char ch: s.toCharArray())
            freq[ch - 'a']++;
        
        for(int i = 0; i < s.length(); i++) {
            char ch = s.charAt(i);
            int index = ch - 'a';
            
            freq[ch - 'a']--;
            
            //use bit-mask to check if char already use or not
            if((usedChar & 1 << (ch -'a')) > 0) {
                continue;
            }
            
            while(!stack.isEmpty() && stack.peek() > ch && freq[stack.peek() - 'a'] > 0) {
                char top = stack.pop();
                usedChar ^= 1 << (top -'a'); //mark char as false not used
            }
           
            stack.push(ch);
            usedChar |= 1 << (ch -'a'); //mark char as true (that means this char is now in used
        }
        
        StringBuilder sb = new StringBuilder();
        
        while(!stack.isEmpty()) {
            sb.append(stack.pop());
        }
        
        return sb.reverse().toString();
    }
}
```

### Reference:
- https://www.youtube.com/watch?v=luCn7p2CIbI
