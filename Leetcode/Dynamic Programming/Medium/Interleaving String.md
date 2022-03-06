### Question:
https://leetcode.com/problems/interleaving-string/

### Algo:
DP

### Sol-1
```
class Solution {
    
    int dp[][];
    
    public boolean isInterleave(String s1, String s2, String s3) {
        
        if((s1.length() + s2.length()) != s3.length())
            return false;
        
        dp = new int[s1.length() + 1][s2.length() + 1];
        
        return isInterleave(s1, s2, s3, 0, 0);   
    }
    
    
    public boolean isInterleave(String s1, String s2, String target, int start1, int start2) {
        
        int targetIndex = start1 + start2;
        
        if(targetIndex >= target.length())
            return true;
        
       
        if(dp[start1][start2] != 0)
            return dp[start1][start2] == 1;
        
        boolean result = false;
        
        if(start1 < s1.length() && s1.charAt(start1) == target.charAt(targetIndex))
            result = isInterleave(s1, s2, target, start1 + 1, start2);
        
        if(result == false && start2 < s2.length() && s2.charAt(start2) == target.charAt(targetIndex))
            result = isInterleave(s1, s2, target, start1, start2 + 1);
            
        dp[start1][start2] = result == true? 1: -1;
        
        return result;
    }
}
```

### Sol-2:
```
class Solution {
    
    public boolean isInterleave(String s1, String s2, String s3) {
        
        int len1 = s1.length();
        int len2 = s2.length();
        
        if((len1 + len2) != s3.length())
            return false;
        
        boolean dp[][] = new boolean[len1 + 1][len2 + 1];
        dp[len1][len2] = true;
        
        for(int i = len1; i >= 0; i--) {
            for(int j = len2; j >= 0; j--) {
                if(i < len1 && s1.charAt(i) == s3.charAt(i + j) && dp[i + 1][j])
                    dp[i][j] = true;
                
                if(j < len2 && s2.charAt(j) == s3.charAt(i + j) && dp[i][j + 1])
                    dp[i][j] = true;
            }
        }
        
        return dp[0][0];
    }
    
}
```
