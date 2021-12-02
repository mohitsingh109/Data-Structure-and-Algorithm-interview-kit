### Question:
https://leetcode.com/problems/ransom-note/

### Algo:
Hash Table

### Sol:
```
class Solution {
    public boolean canConstruct(String ransomNote, String magazine) {
        int[] arr = new int[26];
        
        for(int i = 0; i < ransomNote.length(); i++)
            arr[ransomNote.charAt(i) - 'a']++;
        
        for(int i = 0; i < magazine.length(); i++) {
            if(arr[magazine.charAt(i) - 'a'] == 0)
                continue;
            arr[magazine.charAt(i) - 'a']--;
        }
        
        for(int i = 0; i < 26; i++) {
            if(arr[i] != 0)
                return false;
        }
        
        return true;
    }
}
```
