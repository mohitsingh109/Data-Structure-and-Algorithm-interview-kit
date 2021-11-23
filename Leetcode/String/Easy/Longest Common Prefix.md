### Question:
https://leetcode.com/problems/longest-common-prefix/

### Algo:
1. Vertical scanning
2. Trie (we can use in case of streaming ingestion of string with multiple query)

### Sol:
```
class Solution {
    public String longestCommonPrefix(String[] strs) {
        
        if (strs == null || strs.length == 0) return "";
        
        for (int i = 0; i < strs[0].length() ; i++){
            char c = strs[0].charAt(i);
            for (int j = 1; j < strs.length; j ++) {
                if (i == strs[j].length() || strs[j].charAt(i) != c)
                    return strs[0].substring(0, i);             
            }
        }
        
        return strs[0];
    }
}
```
