### Question:
https://leetcode.com/problems/word-search/

### Algo:
Matrix

### Sol:
```
class Solution {
    public boolean exist(char[][] board, String word) {
        
        char[] wordArray = word.toCharArray();
        
        for(int row = 0; row < board.length; row++) {
            for(int col = 0; col < board[0].length; col++) {
                if(board[row][col] == word.charAt(0) && 
                   backtracking(board, wordArray, 0, row, col))
                    return true;
            }
        }
        return false;
    }
    
    public boolean backtracking(char[][] board, char [] word, int index, int row, int col) {
        if(index == word.length)
            return true;
        
        if(row < 0 || col < 0 || row >= board.length || col >= board[0].length 
           || board[row][col] == '0' || word[index] != board[row][col])
            return false;
        
        char ch = board[row][col];
        board[row][col] = '0';
        
        boolean result = backtracking(board, word, index + 1, row + 1, col) || 
                         backtracking(board, word, index + 1, row - 1, col) ||
                         backtracking(board, word, index + 1, row, col + 1) || 
                         backtracking(board, word, index + 1, row, col - 1);
        
        board[row][col] = ch;
        return result;
    }
}
```
