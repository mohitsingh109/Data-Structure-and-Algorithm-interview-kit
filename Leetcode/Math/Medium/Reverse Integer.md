### Question:
https://leetcode.com/problems/reverse-integer/

### Algo:
Math

### Sol:
```
class Solution {
    public int reverse(int x) {
        int reversed = 0;
    
        // MAX = + 2147483647 (2^31 - 1)
        // MIN = - 2147483648 (-2^31)
        while(x != 0) {
            
            int pop = x % 10;
            x /= 10;
            
            if(reversed > Integer.MAX_VALUE/10 || reversed == Integer.MAX_VALUE/10 && pop > 7)
                return 0;
            
            if(reversed < Integer.MIN_VALUE/10 || reversed == Integer.MIN_VALUE/10 && pop < -8)
                return 0;
            
            reversed = (reversed * 10) + pop;
        }
        
        return reversed;
    }
}
```

### Reference:
- https://www.youtube.com/watch?v=HAgLH58IgJQ
