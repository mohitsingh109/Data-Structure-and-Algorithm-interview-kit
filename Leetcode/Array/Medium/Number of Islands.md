### Question:
https://leetcode.com/problems/number-of-islands/

### Algo:
DFS, Matrix

### Sol:
```
class Solution {
    public int numIslands(char[][] grid) {
        int count = 0;
        if (grid == null) return count;
        for (int i = 0 ; i < grid.length ; i++){
            for (int j = 0 ; j < grid[0].length ; j++){
                if (grid[i][j] == '1') {
                    markVisited(grid, i, j);
                    count++;
                }
            }
        }
        
        return count;
    }
    
    public void markVisited(char[][] grid, int i, int j) {
        if (i < 0 || i >= grid.length || j < 0 || j >= grid[0].length || grid[i][j] == '0') 
            return;
        if (grid[i][j] == '#') return;
        
        grid[i][j] = '#';
    
        markVisited(grid, i-1, j);
        markVisited(grid, i, j-1); 
        markVisited(grid, i, j+1);
        markVisited(grid, i+1, j);
    }
}
```
