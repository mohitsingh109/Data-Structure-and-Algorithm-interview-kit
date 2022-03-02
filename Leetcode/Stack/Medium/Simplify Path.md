### Question:
https://leetcode.com/problems/simplify-path/

### Algo:
String

### Sol:
```
class Solution {
    public String simplifyPath(String path) {
        Deque<String> deque = new LinkedList<>();
        
        for(int i = 0; i < path.length(); i++) {
            
            if(path.charAt(i) == '/')
                continue;
            
            StringBuilder sb = new StringBuilder();
            
            while(i < path.length() && path.charAt(i) != '/') {
                sb.append(path.charAt(i));
                i++;
            }
            
            String currentText = sb.toString();
            
            if(currentText.equals("..")) {
                if(!deque.isEmpty())
                    deque.removeLast();
            }else if(!currentText.equals(".")) {
                deque.addLast(currentText);
            }
        }
        
        StringBuilder result = new StringBuilder();
    
        while(!deque.isEmpty()) {
            result.append("/").append(deque.removeFirst());
        }

        return result.isEmpty() ? "/": result.toString();
    }
}
```
