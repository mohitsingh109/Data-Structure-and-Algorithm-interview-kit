### Question:
https://leetcode.com/problems/find-duplicate-subtrees/


### Algo:
bfs

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
    
    Set<String> visited = new HashSet<>();
    Map<String, TreeNode> valueMapToNode = new HashMap<>();
    
    public List<TreeNode> findDuplicateSubtrees(TreeNode root) {
        postOrderTraversal(root);
        return new ArrayList<>(valueMapToNode.values());
    }
    
    public String postOrderTraversal(TreeNode root) {
        StringBuilder sb = new StringBuilder();
        String leftSubtree = "N";
        String rightSubtree = "N";
        
        if(root.left != null)
            leftSubtree = postOrderTraversal(root.left);
        
        if(root.right != null)
            rightSubtree = postOrderTraversal(root.right);
        
        sb.append(root.val);
        sb.append(",");
        sb.append(leftSubtree);
        sb.append(",");
        sb.append(rightSubtree);
        String subTree = sb.toString();
        saveDuplicateSubTree(subTree, root);
        visited.add(subTree);
        return sb.toString();
    }
    
    public void saveDuplicateSubTree(String subTree, TreeNode root) {
       if(visited.contains(subTree)) {
           valueMapToNode.put(subTree, root);
       }
    }
}
```

### Reference
- https://www.youtube.com/watch?v=q7PDuyArHF0&t=484s
