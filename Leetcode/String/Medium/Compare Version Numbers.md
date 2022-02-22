### Question:
https://leetcode.com/problems/compare-version-numbers/

### Algo:
String

### Sol:
```
class Solution {
    public int compareVersion(String version1, String version2) {
        int i = 0, j = 0;
        
        int value1, value2;
        
        while(i < version1.length() || j < version2.length()) {
            
            value1 = value2 = 0;
            while(i < version1.length() && version1.charAt(i) != '.') {
                value1 = value1 * 10 + (version1.charAt(i++) - '0');
            }
            
            while(j < version2.length() && version2.charAt(j) != '.') {
                value2 = value2 * 10 + (version2.charAt(j++) - '0');
            }
            
            if(value1 != value2)
                return Integer.compare(value1, value2);
            
            i++;
            j++;
        }
        
        return 0;
    }
}
```
