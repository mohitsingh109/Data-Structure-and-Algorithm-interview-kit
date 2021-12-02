### Question:
https://leetcode.com/problems/binary-tree-tilt/

### Algo:
bfs

### Sol:
```
class Solution {
    private int totalTilt = 0;
    
    public int findTilt(TreeNode root) {
        helperBuildTiltTree(root);
        return totalTilt;
    }
    
    public int helperBuildTiltTree(TreeNode root) {
        if(root == null)
            return 0;
        
        int leftSum = helperBuildTiltTree(root.left);
        int rightSum = helperBuildTiltTree(root.right);
        totalTilt += Math.abs(leftSum - rightSum);
        return root.val + leftSum + rightSum;
    }
}
```
