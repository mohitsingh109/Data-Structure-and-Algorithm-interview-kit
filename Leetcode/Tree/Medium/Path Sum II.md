### Question:
https://leetcode.com/problems/path-sum-ii/

### Algo
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
    
    List<List<Integer>> res = new ArrayList<>();
    
    public List<List<Integer>> pathSum(TreeNode root, int targetSum) {
        dfs(new LinkedList<>(), root, targetSum, 0);
        return res;
    }
    
    public void dfs(LinkedList<Integer> list, TreeNode root, int targetSum, int currentSum) {
        if(root == null)
            return;
        
        list.add(root.val);
        currentSum += root.val;
        
        if(root.left == null && root.right == null) {
            if(targetSum == currentSum)
                res.add(new ArrayList<>(list));
                
            list.removeLast();
            return;
        }
        
        dfs(list, root.left, targetSum, currentSum);
        dfs(list, root.right, targetSum, currentSum);
        list.removeLast();
    }
}
```
