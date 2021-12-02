### Question:
https://leetcode.com/problems/leaf-similar-trees/

### Algo:
dfs

### Sol:
```
class Solution {
    public boolean leafSimilar(TreeNode root1, TreeNode root2) {
        List<Integer> l1 = new ArrayList<>();
        List<Integer> l2 = new ArrayList<>();
        populateLeafNode(root1, l1);
        populateLeafNode(root2, l2);
        
        return l1.equals(l2);
    }
    
    public void populateLeafNode(TreeNode root, List<Integer> arr) {
        if(root == null)
            return;
        
        if(root.left == null && root.right == null) {
            arr.add(root.val);
            return;
        }
        
        populateLeafNode(root.left, arr);
        populateLeafNode(root.right, arr);
    }
}
```
