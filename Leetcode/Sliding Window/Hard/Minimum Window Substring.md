### Question:
https://leetcode.com/problems/minimum-window-substring/

### Algo:
Hash Table

### Sol:
```
class Solution {
    public String minWindow(String s, String t) {
        
        Map<Character, Integer> needMap = new HashMap<>();
        Map<Character, Integer> haveMap = new HashMap<>();
        
        int have = 0, startWindow = 0, startIndex = -1, endIndex = -1, minLen = Integer.MAX_VALUE;
        
        for(char ch: t.toCharArray())
            needMap.put(ch, needMap.getOrDefault(ch, 0) + 1);
        
        
        for(int endWindow = 0; endWindow < s.length(); endWindow++) {
            
            char ch = s.charAt(endWindow);
            
            if(needMap.containsKey(ch)) {
                haveMap.put(ch, haveMap.getOrDefault(ch, 0) + 1);
                
                if(haveMap.get(ch).equals(needMap.get(ch)))
                    have++;
                
                while(have == needMap.size()) {
                    int currLen = endWindow - startWindow;
                    if(minLen > currLen) {
                        minLen = currLen;
                        startIndex = startWindow;
                        endIndex = endWindow;
                    }
                    
                    ch = s.charAt(startWindow++);
                    
                    if(haveMap.containsKey(ch)) {
                        haveMap.put(ch, haveMap.get(ch) - 1);
                        
                        if(haveMap.get(ch) < needMap.get(ch))
                            have--;   
                    }
                }
            }
        }
        
        return startIndex == -1? "": s.substring(startIndex, endIndex + 1);
    }
}
```

### Reference
- https://www.youtube.com/watch?v=jSto0O4AJbM
