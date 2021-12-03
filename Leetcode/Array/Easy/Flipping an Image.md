### Question:
https://leetcode.com/problems/flipping-an-image/

### Algo:
Array

### Sol:
```
class Solution {
    public int[][] flipAndInvertImage(int[][] image) {
        for(int row = 0; row < image.length; row++)
            flipAndReverse(image[row]);
        
        return image;
    }
    
    public void flipAndReverse(int arr[]) {
        int start = 0;
        int end = arr.length - 1;
        
        while(start < end) {
            int temp = arr[start] ^ 1;
            arr[start] = arr[end] ^ 1;
            arr[end] = temp;
            start++;
            end--;
        }
        
        if(start == end)
            arr[start] = arr[start] ^ 1;
    }
}
```
