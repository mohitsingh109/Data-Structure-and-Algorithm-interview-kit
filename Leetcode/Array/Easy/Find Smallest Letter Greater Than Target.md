### Question:
https://leetcode.com/problems/find-smallest-letter-greater-than-target/

### Algo:
Binary Search

### Sol:
```
class Solution {
    public char nextGreatestLetter(char[] letters, char target) {
        int n = letters.length;
        if(target >= letters[n-1] || letters[0] > target)
            return letters[0];
        
        int L = 0, R = n - 1;
        
        while(L < R) {
            int mid = L + (R-L)/2;
            
            if(letters[mid] <= target)
                L = mid + 1;
            else 
                R = mid;
        }
        
        return letters[L];
    }
}
```
