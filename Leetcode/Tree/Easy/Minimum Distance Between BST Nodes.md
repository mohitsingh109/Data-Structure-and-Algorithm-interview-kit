### Question:
https://leetcode.com/problems/minimum-distance-between-bst-nodes/

### Algo:
Tree Traversal

### Sol:
```
class Solution {
    Integer prev, ans;
    public int minDiffInBST(TreeNode root) {
        prev = null;
        ans = Integer.MAX_VALUE;
        inorder(root);
        return ans;
    }
    
    public void inorder(TreeNode root) {
        if(root == null)
            return;
        
        inorder(root.left);
        if(prev != null)
            ans = Math.min(ans, root.val - prev);
        
        prev = root.val;
        inorder(root.right);
    }
}
```
