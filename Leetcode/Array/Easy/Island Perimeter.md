### Question:
https://leetcode.com/problems/island-perimeter/

### Algo:
Matrix, dfs, bfs

### Sol(dfs)
```
public class Solution {
    public int islandPerimeter(int[][] grid) {
        if (grid == null) return 0;
        for (int i = 0 ; i < grid.length ; i++){
            for (int j = 0 ; j < grid[0].length ; j++){
                if (grid[i][j] == 1) {
                    return getPerimeter(grid,i,j);
                }
            }
        }
        return 0;
    }
    
    public int getPerimeter(int[][] grid, int i, int j){
        if (i < 0 || i >= grid.length || j < 0 || j >= grid[0].length || grid[i][j] == 0) 
            return 1;
        if (grid[i][j] == -1) return 0;
        
        grid[i][j] = -1;
    
        return getPerimeter(grid, i-1, j) + getPerimeter(grid, i, j-1) + getPerimeter(grid, i, j+1) + getPerimeter(grid, i+1, j);
        
    }
}
```

### Sol(bfs)
```
class Solution {
    public int islandPerimeter(int[][] grid) {
        
        int peri = 0;
        
        for(int i =0; i<grid.length; i++){
            for(int j=0; j<grid[i].length; j++){
                if(grid[i][j] == 1) { 
                    if(j-1<0 || grid[i][j-1] == 0) { //left
                        peri++;
                    }
                    if(j+1 >grid[i].length-1 || grid[i][j+1] == 0){ //right
                        peri++;
                    }
                    if(i-1<0 || grid[i-1][j] ==0){ //top
                        peri++;
                    }
                    if(i+1>grid.length-1 || grid[i+1][j] == 0){ //down
                        peri++;
                    }
                }
            }
        }
        
        return peri;
        
    }
}
```
