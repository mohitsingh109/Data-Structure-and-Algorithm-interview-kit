### Question:
https://leetcode.com/problems/repeated-dna-sequences/

### Algo:
Rolling Hash (Rabin karp algorithm)

### Sol:
```
class Solution {
    public List<String> findRepeatedDnaSequences(String s) {
        Map<String, Integer> map = new HashMap<>();
        StringBuilder sb = new StringBuilder();
        for(int i = 0; i < s.length(); i++) {
            sb.append(s.charAt(i));
            if(sb.length() >= 10) {
                String key = sb.toString();
                map.put(key, map.getOrDefault(key, 0) + 1);
                sb.deleteCharAt(0);
            }
        }
        
        
        List<String> result = new ArrayList<>();
        
        for(Map.Entry<String, Integer> e: map.entrySet()) {
            if(e.getValue() > 1)
                result.add(e.getKey());
        }
        
        return result;
    }
}
```

### Sol(Rolling Hash)
```
The key to solve this problem is that each of the 4 nucleotides can be stored in 2 bits. So the 10-letter-long sequence can be converted to 20-bits-long integer.

class Solution {
    public List<String> findRepeatedDnaSequences(String s) {
        Set<Integer> seen = new HashSet<>();
        Set<String> result = new HashSet<>();
        Map<Character, Integer> hashValue = new HashMap<>(){{
            put('A', 0);
            put('C', 1);
            put('G', 2);
            put('T', 3);
        }};
        
        // take 4 as we have 4 unique character this help to remove collision case
        int fourPow9 = (int)Math.pow(4, 9); 
        int rollingHash = 0;
        
        for(int i = 0; i < s.length(); i++) {
            
            //add letter to window [rollingHash * 4] --> this will bump power of 4 in all letter
            rollingHash = rollingHash * 4 + hashValue.get(s.charAt(i));
            
            if(i >= 9) { // window size is now 10
                if(!seen.add(rollingHash))
                    result.add(s.substring(i - 9, i + 1));
                
                // remove first letter from window
                rollingHash = rollingHash - fourPow9 * hashValue.get(s.charAt(i - 9));   
            }
        }
        
        return new ArrayList<>(result);
    }
}
```
