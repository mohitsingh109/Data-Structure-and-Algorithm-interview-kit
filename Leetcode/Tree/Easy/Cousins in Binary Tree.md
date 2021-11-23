### Question:
https://leetcode.com/problems/cousins-in-binary-tree/

### Algo:
Tree Height

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
    class NodeHeight {
        int height;
        int val;
        TreeNode parent;
        NodeHeight(int height,int val){
            this.height=height;
            this.val=val;
        }
    }
    
    public boolean isCousins(TreeNode root, int x, int y) {
        NodeHeight xNodeHeight = new NodeHeight(0, x);
        NodeHeight yNodeHeight = new NodeHeight(0, y);
        height(root, xNodeHeight, yNodeHeight, 0, null);
        
        return xNodeHeight.height != 0 && xNodeHeight.height == yNodeHeight.height && xNodeHeight.parent != yNodeHeight.parent;
    }
    
    public static void height(TreeNode root, NodeHeight xNodeHeight, NodeHeight yNodeHeight, int depth, TreeNode parent) {
        if(root == null) return;
        
        if(root.val == xNodeHeight.val) {
            xNodeHeight.parent = parent;
            xNodeHeight.height = depth;
        }
        
        if(root.val == yNodeHeight.val) {
            yNodeHeight.parent = parent;
            yNodeHeight.height = depth;
        }
        
        height(root.left, xNodeHeight, yNodeHeight, depth + 1, root);
        height(root.right, xNodeHeight, yNodeHeight, depth + 1, root);
    }
}
```
