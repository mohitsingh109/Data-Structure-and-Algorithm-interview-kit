### Question:
https://leetcode.com/problems/surrounded-regions/

### Algo:
dfs

### Sol:
```
class Solution {
    public void solve(char[][] board) {
        
        for(int i = 0; i < board[0].length; i++) {
            if(board[0][i] == 'O')
                dfs(board, 0, i);
            
            if(board[board.length - 1][i] == 'O')
                dfs(board, board.length - 1, i);
        }
        
        for(int i = 0; i < board.length; i++) {
            if(board[i][0] == 'O')
                dfs(board, i, 0);
            
            if(board[i][board[0].length - 1] == 'O')
                dfs(board, i, board[0].length - 1);
        }
        
        
        
        for(int row = 0; row < board.length; row ++) {
            for(int col = 0; col < board[0].length; col++) {
                if(board[row][col] == '#')
                    board[row][col] = 'O';
                else if(board[row][col] == 'O')
                    board[row][col] = 'X';
            }
        }
    }
    
    public void dfs(char[][] board, int row, int col) {
        
        if(row < 0 || row >= board.length || col < 0 || col >= board[0].length)
            return;
        
        if(board[row][col] == '#' || board[row][col] == 'X')
            return;
        
        board[row][col] = '#';
        
        dfs(board, row - 1, col);
        dfs(board, row + 1, col); 
        dfs(board, row, col + 1);
        dfs(board, row, col - 1);       
    }
    
}
```
