### Question:
https://leetcode.com/problems/spiral-matrix/

### Algo:
Matrix

### Sol:
```
class Solution {
    public List<Integer> spiralOrder(int[][] matrix) {
        int r1 = 0;
        int r2 = matrix.length - 1;
        int c1 = 0;
        int c2 = matrix[0].length - 1;
        int dir = 0;
        
        List<Integer> result = new ArrayList<>();
        
        while(r1 <= r2 && c1 <= c2) {
            if(dir == 0) {
                for(int i = c1; i <= c2; i++)
                    result.add(matrix[r1][i]);
                  r1++;
                dir = 1;
            } else if(dir == 1) {
                 for(int i = r1; i <= r2; i++)
                    result.add(matrix[i][c2]);
                 c2--;
                dir = 2;
            }else if(dir == 2) {
               for(int i = c2; i>= c1; i--)
                 result.add(matrix[r2][i]); 
                r2--;
                dir = 3;
            } else {
                 for(int i = r2; i >= r1; i--)
                    result.add(matrix[i][c1]);
                 c1++;
                dir = 0;
            } 
        }
        
        return result;
    }
}
```
