### Question:
https://leetcode.com/problems/subtree-of-another-tree/

### Algo:
dfs

### Sol:
```
class Solution {
    public boolean isSubtree(TreeNode root, TreeNode subRoot) {
        if(root == null)
            return subRoot == null;
        
        if(checkTwoTreeAreEqual(root, subRoot))
            return true;
        
        return isSubtree(root.left, subRoot) || isSubtree(root.right, subRoot);
    }
    
    public boolean checkTwoTreeAreEqual(TreeNode tree1, TreeNode tree2) {
        if(tree1 == null && tree2 == null)
            return true;
        
        if(tree1 == null || tree2 == null)
            return false;
        
        return tree1.val == tree2.val && checkTwoTreeAreEqual(tree1.left, tree2.left) && checkTwoTreeAreEqual(tree1.right, tree2.right);
    }
}
```
