### Question:
https://leetcode.com/problems/peak-index-in-a-mountain-array/

### Algo:
Binary Search

### Sol:
```
class Solution {
   public int peakIndexInMountainArray(int[] A) {
        int lo = 0, hi = A.length - 1;
        while (lo < hi) {
            int mi = lo + (hi - lo) / 2;
            if (A[mi] < A[mi + 1])
                lo = mi + 1;
            else
                hi = mi;
        }
        return lo;
    }
}
```
