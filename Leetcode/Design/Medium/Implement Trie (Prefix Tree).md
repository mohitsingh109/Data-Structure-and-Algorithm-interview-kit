### Question:
https://leetcode.com/problems/implement-trie-prefix-tree/

### Algo:
Prefix Tree, Trie

### Sol:
```
class TrieNode {
    private static final int CHARACTER_SIZE = 26; 
    TrieNode[] nodes = new TrieNode[CHARACTER_SIZE];
    boolean isWord;
}

class Trie {
    
    private TrieNode head;

    public Trie() {
        this.head = new TrieNode();
    }
    
    public void insert(String word) {
        TrieNode crwl = head;
        
        for(char ch: word.toCharArray()) {
            int index = ch - 'a';
            if(crwl.nodes[index] == null)
                crwl.nodes[index] = new TrieNode();
            crwl = crwl.nodes[index];
        }
        
        crwl.isWord = true;
    }
    
    public boolean search(String word) {
        TrieNode crwl = head;
        
        for(char ch: word.toCharArray()) {
            int index = ch - 'a';
            if(crwl.nodes[index] == null)
                return false;
            crwl = crwl.nodes[index];
        }
        
        return crwl.isWord;
    }
    
    public boolean startsWith(String prefix) {
        TrieNode crwl = head;
        
        for(char ch: prefix.toCharArray()) {
            int index = ch - 'a';
            if(crwl.nodes[index] == null)
                return false;
            crwl = crwl.nodes[index];
        }
        
        return true;
    }
}
```
