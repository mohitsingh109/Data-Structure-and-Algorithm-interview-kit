### Question:
https://leetcode.com/problems/check-completeness-of-a-binary-tree/

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
    
    public boolean isCompleteTree(TreeNode root) {
        Queue<TreeNode> queue = new LinkedList<>();
        queue.add(root);
        boolean end = false;
        
        while(!queue.isEmpty()) {
            TreeNode node = queue.remove();
            
           if(node == null)
               end = true;
            else {
                if(end) return false;
                queue.add(node.left);
                queue.add(node.right); 
            }
        }
        
        return true;
    }
}
```
