### Question:
https://leetcode.com/problems/increasing-order-search-tree/

### Algo:
Tree Traversal

### Sol:
```
class Solution {
    TreeNode curr;
    public TreeNode increasingBST(TreeNode root) {
        TreeNode ans = new TreeNode(-1);
        curr = ans;
        inorder(root);
        return ans.right;
    }
    
    public void inorder(TreeNode root) {
        if(root == null)
            return;
        
        inorder(root.left);
        root.left = null;
        curr.right = root;
        curr = root;
        inorder(root.right); 
    }
}
```
