### Question:
https://leetcode.com/problems/diameter-of-binary-tree/

### Algo:
dfs

### Sol:
```
class Solution {
    int diameter = 0;
    public int diameterOfBinaryTree(TreeNode root) {
        height(root);
        return diameter;
    }
    
    public int height(TreeNode root) {
        if(root == null)
            return 0;
        
        int lHeight = height(root.left);
        int rHight = height(root.right);
        int currDiameter = lHeight + rHight;
        diameter = Math.max(diameter, currDiameter);
        return Math.max(lHeight, rHight) + 1;
    }
}
```
