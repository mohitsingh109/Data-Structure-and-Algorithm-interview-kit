### Question:
https://leetcode.com/problems/minimum-difficulty-of-a-job-schedule/


### Algo:
Array

### Sol:
```
class Solution {
    Integer [][]dp;
    public int minDifficulty(int[] jobDifficulty, int d) {
        dp = new Integer[jobDifficulty.length][d + 1];
        return rec(jobDifficulty, 0, d);
    }
    
    public int rec(int[] jobs, int index, int d) {
        
        if(d <= 0 || index >= jobs.length)
            return -1;
        
        if(dp[index][d] != null)
            return dp[index][d];
        
        int maxDayDifficulty = 0;
        int minDifficulty = Integer.MAX_VALUE;
        
        for(int i = index; i <= jobs.length - d; i++) {
            maxDayDifficulty = Math.max(maxDayDifficulty, jobs[i]);
            int ans = rec(jobs, i + 1, d - 1);
            if(ans != -1)
                minDifficulty = Math.min(minDifficulty, maxDayDifficulty + ans);
        }
        
        if(d == 1)
            return maxDayDifficulty;
       
        
        dp[index][d] = minDifficulty == Integer.MAX_VALUE? -1:  minDifficulty;
        return dp[index][d];
    }
}
```

### Sol-2:
```
class Solution {
 
    public int minDifficulty(int[] jobDifficulty, int d) {
        int jobs = jobDifficulty.length;
        
        if(d > jobs) return -1;
        
        int [][] dp = new int[d][jobs];
        
        // calculate minimum difficulty with d = 1
        dp[0][0] = jobDifficulty[0];
        
        for(int i = 1; i < jobs; i++)
            dp[0][i] = Math.max(dp[0][i - 1], jobDifficulty[i]);
        
        
        // calculate minimum difficulty for each day
        for(int i = 1; i < d; i++) {
            
            for(int j = i; j < jobs; j++) {
                int max = 0;
                dp[i][j] = Integer.MAX_VALUE;
                
                // for day d at job k
                // dp[d][k] = Math.min(dp[d][k], dp[d - 1][k - 1] + Max(jobDifficulty[k : n]))
                for(int k = j; k >= i; k--) {
                   max = Math.max(max, jobDifficulty[k]);
                   dp[i][j] = Math.min(dp[i][j] , dp[i - 1][k - 1] + max);
                }
            }
        }
        
        
        return dp[d - 1][jobs - 1];
    }
}
```
