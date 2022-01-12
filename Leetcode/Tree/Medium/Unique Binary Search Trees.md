### Question:
https://leetcode.com/problems/unique-binary-search-trees/

### Algo:
DP, Math

### Sol:
```
class Solution {
    public int numTrees(int n) {
        int[] dp = new int[n + 1];
        
        dp[0] = dp[1] = 1;
        
        for(int i = 2; i<=n; i++) {
            for(int j = 0; j < i; j++) {
                dp[i] += dp[j] * dp[i -j -1];
            }
        }
        
        return dp[n];
    }
}

/*

T[1] = 1
T[2] = 2
T[3] = [
    element = {1, 2, 3}
    
    1 as root = T[0] * T[2] // left size 0 element, right side 2 element
    2 as root = T[1] * T[1] // left, right size has 1 element
    3 as root = T[2] * T[0] // left size 2 element, right side 0 element
    
    T[3] = T[0] * T[2] + T[1] * T[1] + T[2] * T[0]
    T[3] = 2 + 1 + 2 = 5
] 

Note: This number we call catalan number

*/
```

### Reference:
- https://www.youtube.com/watch?v=Ox0TenN3Zpg
- https://www.youtube.com/watch?v=YDf982Lb84o
