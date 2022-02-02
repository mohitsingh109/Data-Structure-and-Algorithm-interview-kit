### Question:
https://leetcode.com/problems/binary-tree-maximum-path-sum/

### Algo:
dfs

### Sol:
```
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    int maxSum = Integer.MIN_VALUE;
    
    public int maxPathSum(TreeNode root) {
        maxPathSumInternal(root);
        return maxSum;
    }
    
    public int maxPathSumInternal(TreeNode root) {
        if(root == null)
            return 0;
        
        int leftSum = maxPathSumInternal(root.left);
        int rightSum = maxPathSumInternal(root.right);
        
        int maxSplit = Math.max(leftSum, rightSum);
        int maxSumSoFar = Math.max(leftSum + rightSum, maxSplit) + root.val;
        maxSumSoFar = Math.max(maxSumSoFar, root.val);
        
        if(maxSumSoFar > maxSum)
            maxSum = maxSumSoFar;
        
        return root.val + Math.max(0, maxSplit);
    }
}
```
