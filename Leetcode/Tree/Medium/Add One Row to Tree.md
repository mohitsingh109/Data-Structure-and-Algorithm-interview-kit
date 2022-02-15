### Question:
https://leetcode.com/problems/add-one-row-to-tree/

### Algo:
dfs

### Sol:
```
class Solution {
    public TreeNode addOneRow(TreeNode root, int val, int depth) {
        return addOneRow(root, val, depth, true);
    }
    
     public TreeNode addOneRow(TreeNode root, int val, int depth, boolean isLeft) {
        if(depth == 1)
            return isLeft? new TreeNode(val , root, null):  new TreeNode(val , null, root);
         
        if(root == null)
            return null;
        
        root.left = addOneRow(root.left , val, depth - 1, true);
        root.right = addOneRow(root.right , val, depth - 1, false);
        return root;
    }
}
```
