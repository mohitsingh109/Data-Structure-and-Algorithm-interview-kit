### Question:
https://leetcode.com/problems/group-anagrams/

### Algo:
Sorting

### Sol:
```
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        
        Map<String, List<String>> anagramsMap = new HashMap<>();
        
        for(int i = 0; i < strs.length; i++) {
            char[] sortedCh = strs[i].toCharArray();
            Arrays.sort(sortedCh);
            String strSorted = new String(sortedCh);
            anagramsMap.putIfAbsent(strSorted, new ArrayList<>());
            anagramsMap.get(strSorted).add(strs[i]);
        }
        
       return new ArrayList<>(anagramsMap.values());
    }
}
```
