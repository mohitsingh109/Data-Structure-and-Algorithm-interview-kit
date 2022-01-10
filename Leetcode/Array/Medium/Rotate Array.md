### Question:
https://leetcode.com/problems/rotate-array/

### Algo:
Math, Two Pointer

### Sol:
```
class Solution {
    public void rotate(int[] arr, int k) {
        int len = arr.length;
        k = k % len;
        int lastIndex = len - k;
        reverse(arr, 0, lastIndex - 1);
        reverse(arr, lastIndex, len - 1);
        reverse(arr, 0, len - 1);
    }
    
    public void reverse(int[] arr, int s, int e) {
        while(s <= e) {
            int temp = arr[s];
            arr[s] = arr[e];
            arr[e] = temp;
            s++;
            e--;
        }
    }
}
```
