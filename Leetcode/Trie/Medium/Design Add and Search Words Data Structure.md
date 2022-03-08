### Question:
https://leetcode.com/problems/design-add-and-search-words-data-structure/

### Algo:
dfs

### Sol:
```
public class Trie {
    private static final int SIZE = 26;
    Trie[] children = new Trie[SIZE];
    boolean isWord;
    
    public void insert(String word) {
        Trie crawler = this;
        for(char ch: word.toCharArray()) {
            int index = ch - 'a';
            if(crawler.children[index] == null)
                crawler.children[index] = new Trie();
            
            crawler = crawler.children[index];
        }
        
        crawler.isWord = true;
    }
    
    public boolean search1(char[] arr, int index, Trie crawler) {
        if(index == arr.length)
            return crawler.isWord;
        
        if(Character.isLetter(arr[index])) {
            int cIndex = arr[index] - 'a';
            if(crawler.children[cIndex] == null)
                return false;
            
            return search1(arr, index + 1, crawler.children[cIndex]);
        }

        for(int i = 0; i < SIZE; i++) {
            if(crawler.children[i] != null && search1(arr, index + 1, crawler.children[i]))
                return true;
        }
        
        return false;
    }
    
    public boolean search2(String word) {
        Trie curr = this;
        for(int i = 0; i < word.length(); ++i){
            char c = word.charAt(i);
            if(c == '.'){
                for(Trie ch: curr.children)
                    if(ch != null && ch.search2(word.substring(i+1))) return true;
                return false;
            }
            if(curr.children[c - 'a'] == null) return false;
            curr = curr.children[c - 'a'];
        }
        return curr != null && curr.isWord;
    }
}


class WordDictionary {
    
    private Trie root;

    public WordDictionary() {
        root = new Trie();
    }
    
    public void addWord(String word) {
        root.insert(word);
    }
    
    public boolean search(String word) {
        //return root.search1(word.toCharArray(), 0, root);
        return root.search2(word);
    }
}

/**
 * Your WordDictionary object will be instantiated and called as such:
 * WordDictionary obj = new WordDictionary();
 * obj.addWord(word);
 * boolean param_2 = obj.search(word);
 */
```
