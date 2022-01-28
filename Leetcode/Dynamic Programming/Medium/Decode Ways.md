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

### Sol: (iterative)
```
class Solution {
    public int numDecodings(String s) {
        
        //dp[i] = dp[i + 1] + dp[i + 2];
        
        int len = s.length();
        int[] dp = new int[len + 1];
        
        dp[len] = 1;
        dp[len - 1] = s.charAt(len -1) == '0'? 0: 1;
        
        for(int index = len - 2; index >=0; index--) {
            if(s.charAt(index) == '0')
                dp[index] = 0;
            else dp[index] = dp[index + 1];
            
            if((index + 1) < len && (s.charAt(index) == '1' || (s.charAt(index) == '2' && s.charAt(index + 1) <= '6'))) {
                dp[index] += dp[index + 2];
            } 
        }
        
        return dp[0];
    }
}
```
