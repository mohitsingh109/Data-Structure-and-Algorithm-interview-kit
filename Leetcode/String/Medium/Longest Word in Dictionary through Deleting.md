### Question:
https://leetcode.com/problems/longest-word-in-dictionary-through-deleting/

### Algo:
String manipulate

### Sol:
```
class Solution {
    public String findLongestWord(String s, List<String> dictionary) {
        String result = "";
    
        for(String str: dictionary) {
            if(result.length() <= str.length()) {
                if(isValid(s, str)) {
                    if(result.isEmpty() || result.length() < str.length() || result.compareTo(str) > 0) {
                        result = str;
                    }
                }
            }
        }
        
        return result;
    }
    
    public boolean isValid(String source, String target) {
        if(target.length() > source.length())
            return false;
        
        int i = 0, j = 0;
        
        while(i < source.length() && j < target.length()) {
            if(source.charAt(i) == target.charAt(j))
                j++;
            
             i++;
        }
        
        return j == target.length();
    }
}
```
