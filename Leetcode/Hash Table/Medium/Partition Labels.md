### Question:
https://leetcode.com/problems/partition-labels/

### Algo:
Greedy

### Sol:
```
class Solution {
    public List<Integer> partitionLabels(String s) {
        Map<Character, Integer> map = new HashMap<>();
        List<Integer> result = new ArrayList<>();
        
        
        for(int i = 0; i < s.length(); i++) {
            char ch = s.charAt(i);
            map.put(ch, i);
        }
        
        int start = 0;
        
        while(start < s.length()) {
            int endIndex = map.get(s.charAt(start));
            
            for(int j = start + 1; j <= endIndex; j++) {
                endIndex = Math.max(endIndex, map.get(s.charAt(j)));
            }
            
            result.add(endIndex - start + 1);
            start = endIndex + 1;
        }
        
        return result;
    }
}
```
