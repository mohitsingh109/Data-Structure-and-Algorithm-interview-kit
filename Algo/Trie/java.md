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
    
    public boolean search(String key) {
 
        Trie curr = this;
 
        for (char c: key.toCharArray()) {
            int index = ch - 'a';
            curr = curr.children[index];
            
            if (curr == null)
                return false;
        }
        
        return curr.isLeaf;
    }
}
```
