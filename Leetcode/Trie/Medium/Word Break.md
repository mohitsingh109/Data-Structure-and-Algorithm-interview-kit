### Question:
https://leetcode.com/problems/word-break/

### Algo:
Trie, Hash Table, Memoization, DP

### Sol:
```
public class Trie {
    static final int ALPHABET_SIZE = 26;
    boolean isEndOfWord;
    Trie[] children = new Trie[ALPHABET_SIZE];
    
    public void insert(String key) {
        Trie curr = this;
 
        for (char ch: key.toCharArray()){
            int index = ch - 'a';
            if (curr.children[index] == null)
                curr.children[index] = new Trie();
 
            curr = curr.children[index];
        }
 
        curr.isEndOfWord = true;
    }
    
    public Trie searchNodeByNode(char key, Trie curr) {
        int index = key - 'a';
        curr = curr.children[index];
        return curr;
    }
}

class Solution {
    
    Set<Integer> indexSeen = new HashSet<>();
    
    public boolean wordBreak(String s, List<String> wordDict) {
        Trie root = new Trie();
        for(String word: wordDict)
            root.insert(word);
        
        
        return validWordBreak(root, 0, s);
    }
    
    public boolean validWordBreak(Trie root, int index, String str) {
        if(index == str.length())
            return true;
        
        if(indexSeen.contains(index))
            return false;
        
        indexSeen.add(index);
        
        Trie curr = root;
        for(int start = index; start < str.length(); start++) {
            curr = curr.searchNodeByNode(str.charAt(start), curr);
            if(curr == null)
                return false;
            
            if(curr.isEndOfWord == true && validWordBreak(root, start + 1, str))
                return true;
        }
        
        return false;
    }
}
```
