### Question:
https://leetcode.com/problems/distribute-coins-in-binary-tree/

### Algo:
dfs

### Sol:
```
class Solution {
    int ans = 0;
    
    public int distributeCoins(TreeNode root) {
        dfs(root);
        return ans;
    }
    
    public int dfs(TreeNode root) {
        
        if(root == null)
            return 0;
        
        int left = dfs(root.left);
        int right = dfs(root.right);
        
        int currentValue = left + right + root.val - 1;
        ans += Math.abs(left) + Math.abs(right) + root.val - 1;
        return currentValue;
    }
}
```
