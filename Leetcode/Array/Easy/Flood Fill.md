### Question:
https://leetcode.com/problems/flood-fill/

### Algo:
Array, dfs, Matrix

### Sol:
```
class Solution {
    public int[][] floodFill(int[][] image, int sr, int sc, int newColor) {
        int currentColor = image[sr][sc];
        if(currentColor != newColor)
            floodFill(image, currentColor, sr, sc, newColor);
        return image;
    }
    
    public void floodFill(int[][] image, int val, int row, int col, int newColor) {
        if(row < 0 || row >= image.length || col < 0 || col >= image[0].length || val != image[row][col])
            return;
        
      
        image[row][col] = newColor;
        floodFill(image, val, row + 1, col, newColor);
        floodFill(image, val, row - 1, col, newColor);
        floodFill(image, val, row, col + 1, newColor);
        floodFill(image, val, row, col - 1, newColor);
    }
}
```
