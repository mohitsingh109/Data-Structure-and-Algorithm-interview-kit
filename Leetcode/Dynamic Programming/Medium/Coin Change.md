### Question:
https://leetcode.com/problems/coin-change/

### Algo:
Array, DP

### Sol: (Top Down)
```
/**
 * Dynamic programming - Top Down (Recursive Approach)
 *
 * change[i] - minimum number of coins needed to make change for amount i using
 * given coin denominations. Each value in change array is calculated only once.
 *
 * Time Complexity: O(C * A). In the worst case the recursive tree has height A
 * and the algorithm solves only A sub problems because it caches precalculated
 * solutions in a table. Each sub problem is computed with C iterations, one by
 * each coin denomination. Thus, TC = O(C * A).
 *
 * Space Complexity: O(A). --> Taken by HashMap and Recursion Depth.
 *
 * C = Number of coin denominations. A = Input amount.
 */
 
class Solution {
    public int coinChange(int[] coins, int amount) {
        if (amount == 0) {
            return 0;
        }
        if (coins == null || coins.length == 0 || amount < 0) {
            return -1;
        }

        HashMap<Integer, Integer> map = new HashMap<>();

        int result = coinChangeHelper(coins, amount, map);
        return result == Integer.MAX_VALUE ? -1 : result;
    }

    /**
     * @return Integer.MAX_VALUE if no combination is possible
     */
    private int coinChangeHelper(int[] coins, int amount, HashMap<Integer, Integer> map) {
        if (amount == 0) {
            return 0;
        }
        if (map.containsKey(amount)) {
            return map.get(amount);
        }

        int minCount = Integer.MAX_VALUE;
        for (int c : coins) {
            if (amount >= c) {
                int count = coinChangeHelper(coins, amount - c, map);
                if (count != Integer.MAX_VALUE) {
                    minCount = Math.min(minCount, coinChangeHelper(coins, amount - c, map) + 1);
                }
            }
        }

        map.put(amount, minCount);
        return map.get(amount);
    }
}
```

### Sol: (Bottom up)
```
/**
 * Dynamic programming - Bottom up (Iterative Approach)
 *
 * DP[i][j] - minimum number of coins needed to make amount j using upto ith coins.
 * DP[i][j] = Math.min(DP[i-1][j], DP[i][ j-coins[i] ] + 1)
 *            DP[i-1][j]==> Not using ith coin.
 *            DP[i][ j-coins[i] ] + 1 ==> Using ith coin. j-coins[i] >= 0
 *
 * Time Complexity: O(C * A)
 *
 * Space Complexity: O(A). DP array.
 *
 * C = Number of coin denominations. A = Input amount.
 */
class Solution {
    public int coinChange(int[] coins, int amount) {
        if (amount == 0) {
            return 0;
        }
        if (coins == null || coins.length == 0 || amount < 0) {
            return -1;
        }

        int[] dp = new int[amount + 1];
        Arrays.fill(dp, Integer.MAX_VALUE);
        dp[0] = 0;

        for (int c : coins) {
            for (int i = c; i <= amount; i++) {
                if (dp[i - c] != Integer.MAX_VALUE) {
                    dp[i] = Math.min(dp[i], dp[i - c] + 1);
                }
            }
        }

        return dp[amount] == Integer.MAX_VALUE ? -1 : dp[amount];
    }
}
```
