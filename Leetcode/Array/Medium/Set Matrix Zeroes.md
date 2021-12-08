### Question:
https://leetcode.com/problems/set-matrix-zeroes/

### Algo:
Matrix

### Ref:
https://www.youtube.com/watch?v=M65xBewcqcI

### Sol:
```
class Solution {
    public void setZeroes(int[][] matrix) {
        
        boolean col0 = false; 
        
        for(int row = 0; row < matrix.length; row++) {
            if(matrix[row][0] == 0) col0 = true;
            for(int col = 1; col < matrix[0].length; col++) {
                if(matrix[row][col] == 0)
                    matrix[0][col] = matrix[row][0] = 0;
            }
        }
        
        for(int row = matrix.length - 1; row >= 0; row--) {
            for(int col = matrix[0].length - 1; col > 0; col--) {
                if(matrix[row][0] == 0 || matrix[0][col] == 0)
                    matrix[row][col] = 0;
            }
            
            if(col0) matrix[row][0] = 0;
        }
    }
}
```
