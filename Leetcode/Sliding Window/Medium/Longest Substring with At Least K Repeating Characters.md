### Question:
https://leetcode.com/problems/longest-substring-with-at-least-k-repeating-characters/

### Algo:
Hash Map, Divide & Conquer

### Sol(Divide & Conquer):
```
class Solution {
    public int longestSubstring(String s, int k) {
        return countK(s.toCharArray(), 0, s.length(), k);
    }
    
    public int countK(char[] arr, int start, int end, int k) {
         if(k > (end - start))
             return 0;
        
         int[] count = new int[26];
        
         for(int i = start; i < end; i++)
             count[arr[i] - 'a']++;
        
        for(int i = start; i < end; i++) {
            if(count[arr[i] - 'a'] < k) {
                return Math.max(countK(arr, start, i, k), countK(arr, i + 1, end, k));
            }
        }
        
        return end - start;
    }
    
}
```

### Sol(Sliding window):
```

```
