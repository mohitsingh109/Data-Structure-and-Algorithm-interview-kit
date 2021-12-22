### Question:
https://leetcode.com/problems/valid-sudoku/

### Algo:
Matrix

### Sol:
```
class Solution {
    public boolean isValidSudoku(char[][] board) {
        Set seen = new HashSet();
        for (int i=0; i<9; ++i) {
            for (int j=0; j<9; ++j) {
                char number = board[i][j];
                if (number != '.')
                    if (!seen.add(number + " in row " + i) ||
                        !seen.add(number + " in column " + j) ||
                        !seen.add(number + " in block " + i/3 + "-" + j/3))
                        return false;
            }
        }
        return true;
    }
}
```

### Sol:
```
class Solution {
    public boolean isValidSudoku(char[][] board) {
        for(int i = 0; i < 9; i++) {
            for(int j = 0; j < 9; j++) {
                if(board[i][j] != '.') {
                    char ch = board[i][j];
                    board[i][j] = '.';
                    if(!isValidPosition(ch, board, i, j))
                        return false;
                    board[i][j] = ch;
                }
            }
        }
        
        return true;
    }
    
    
    public boolean isValidPosition(char ch, char[][] board, int row, int col) {
        for(int i = 0; i < 9; i++) {
            if(board[i][col] == ch || board[row][i] == ch)
                return false;
        }
        
        int boxRow = (row/3) * 3;
        int boxCol = (col/3) * 3;
        
        for(int r = 0; r < 3; r ++) {
            for(int c = 0; c < 3; c ++) {
                if(board[r + boxRow][c + boxCol] == ch)
                    return false;
            }
        }
        
        return true;
    }
}

```
