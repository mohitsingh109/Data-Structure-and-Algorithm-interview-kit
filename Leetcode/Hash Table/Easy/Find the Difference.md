### Question:
https://leetcode.com/problems/find-the-difference/

### Algo:
Hash Table, XOR

### Sol-1:
```
class Solution {
    public char findTheDifference(String s, String t) {
        int[] charCount = new int[26];
        
        for(int i = 0; i < s.length(); i++)
            charCount[s.charAt(i)-'a']++;
        
        for(int i = 0; i < t.length(); i++)
            charCount[(t.charAt(i)-'a')]--;
        
        char ch = 'a';
        for(int i = 0 ; i < 26; i++) {
            if(charCount[i] == -1) {
                ch +=i;
                break;
            }
        }
                
        return ch;
    }
}
```

### Sol-2:
```
class Solution {
    public char findTheDifference(String s, String t) {
        char ch = 0;
        String concatStr = s + t;
        for(int i = 0 ; i < concatStr.length(); i++)
            ch ^= concatStr.charAt(i);
        return ch;
    }
}
```
