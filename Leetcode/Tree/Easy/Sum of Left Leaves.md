### Question:
https://leetcode.com/problems/sum-of-left-leaves/

### Algo:
bfs

### Sol:
```
class Solution {
    public int sumOfLeftLeaves(TreeNode root) {
        
        return helperSumOfLeftLeaves(root, false);
    }
    
    public int helperSumOfLeftLeaves(TreeNode root, boolean isLeft) {
        if(root == null)
            return 0;
        
        if(isLeft && root.left == null && root.right == null)
            return root.val;
        
        return helperSumOfLeftLeaves(root.left, true) + helperSumOfLeftLeaves(root.right, false);
        
    }
}
```
