### Question:
https://leetcode.com/problems/maximum-product-of-word-lengths/

### Algo:
String, Bitwise operator

### Sol:
```
class Solution {
    public int maxProduct(String[] words) {
        int[] bits = new int[words.length];
        int res = 0;
        
        for(int i = 0; i < words.length; i++) {
             int or = 0;
            
            for(char ch: words[i].toCharArray())
                or = or | 1 << (ch - 'a');
            
             bits[i] = or;
        }
        
        
        for(int i = 0; i < bits.length; i++) {
            for(int j = i + 1; j < bits.length; j++) {
                if((bits[i] & bits[j]) == 0)
                    res = Math.max(res, words[i].length() * words[j].length());
            }
        }
        
        return res;
    }
}
```
