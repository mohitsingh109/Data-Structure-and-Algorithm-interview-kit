### Question:
https://leetcode.com/problems/decode-ways/

### Algo:
String

### Sol (Recursions):
```
class Solution {
    int dp[];
    public int numDecodings(String s) {
        
        dp = new int[s.length()];
        Arrays.fill(dp, -1);
        
        return backTrack(s.toCharArray(), 0);
    }
    
    
    public int backTrack(char[] arr ,int index) {
        if(arr.length <= index)
            return 1;
        
        if(dp[index] != -1)
            return dp[index];
        
        if(arr[index] == '0')
            return 0;
        
        int count = backTrack(arr, index + 1);
        
        if((index + 1) < arr.length && (arr[index] == '1' || (arr[index] == '2' && arr[index + 1] <= '6'))) {
            count += backTrack(arr, index + 2);
        } 
        
        dp[index] = count;
        return dp[index];
    }
}
```
