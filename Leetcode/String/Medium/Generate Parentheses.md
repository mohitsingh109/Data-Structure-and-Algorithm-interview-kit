### Question:
https://leetcode.com/problems/generate-parentheses/

### Algo:
Backtracking

### Sol:
```
class Solution {
    public List<String> generateParenthesis(int n) {
        List<String> res = new LinkedList<>();
        backtrack(new StringBuilder(), n, n, res);
        return res;
    }
    
    public void backtrack(StringBuilder text, int open, int close, List<String> res) {
        
        if(open + close == 0) {
            res.add(text.toString());
            return;
        }
        
       if(open > 0) {
           text.append("(");
           backtrack(text, open - 1, close, res);
           text.deleteCharAt(text.length() - 1);
       }
        
        if(close > 0 && close > open) {
            text.append(")");
            backtrack(text, open, close - 1, res);
            text.deleteCharAt(text.length() - 1);
        }
    }
}
```
