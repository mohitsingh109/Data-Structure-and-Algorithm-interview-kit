### Question:
https://leetcode.com/problems/assign-cookies/

### Algo:
Array, Sorting, Greedy

### Sol:
```
class Solution {
    public int findContentChildren(int[] g, int[] s) {
        Arrays.sort(g);
        Arrays.sort(s);
        
        int count = 0;
        int gItr = 0;
        int sItr = 0;
        while(gItr < g.length && sItr < s.length) {
            if(s[sItr] >= g[gItr]) {
                count++;
                gItr++;
            }
            
            sItr++;
        }
        
        return count;
    }
}
```
