### Question:
https://leetcode.com/problems/find-all-anagrams-in-a-string/

### Algo:
Hash Table

### Sol:
```
class Solution {
    public List<Integer> findAnagrams(String s, String p) {
        int[] search = new int[26];
        int[] window = new int[26];
        List<Integer> result = new ArrayList<>();
        for(char ch: p.toCharArray())
            search[ch - 'a']++;
        
        int startWindow = 0;
        
        for(int endWindow = 0; endWindow < s.length(); endWindow++) {
            window[s.charAt(endWindow) - 'a']++;
            
            if(endWindow + 1 >= p.length()) {
    
                if(Arrays.equals(search, window))
                    result.add(startWindow);
                
                window[s.charAt(startWindow++) - 'a']--;
            }
        }
        
        return result;
    }
}
```
