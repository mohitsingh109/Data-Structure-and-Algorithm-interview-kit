### Question:
https://leetcode.com/problems/longest-univalue-path/

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
    
    int len = 0;
    
    public int longestUnivaluePath(TreeNode root) {
       universalPath(root);
       return len;
    }
    
    
    public int universalPath(TreeNode root) {
        
        if(root == null)
            return 0;
        
        int left = universalPath(root.left);
        int right = universalPath(root.right);
        int leftLen = 0;
        int rightLen = 0;
        
        if(root.left != null && root.val == root.left.val) {
            leftLen += left + 1;
        }
        
        if(root.right != null && root.val == root.right.val) {
            rightLen +=  right + 1;
        }
        
        len = Math.max(len, leftLen + rightLen);
        
        return Math.max(leftLen, rightLen);
    } 
}
```
