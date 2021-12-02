### Question:
https://leetcode.com/problems/word-pattern/

### Algo:
Hash Map

### Sol:
```
class Solution {
    public boolean wordPattern(String pattern, String s) {
        String[] word = s.split(" ");
        if(word.length != pattern.length())
            return false;
        
        Map<Character, String> seen = new HashMap<>();
        Set<String> set = new HashSet<>();
        
        for(int i = 0; i < word.length; i++){
            char ch = pattern.charAt(i);
            String str = word[i];
            
            if(!seen.containsKey(ch) && !set.add(str))
                return false;
            
            seen.putIfAbsent(ch, str);
            
            if(!seen.get(ch).equals(str))
                return false;
        }
        
        return true;
    }
}
```
