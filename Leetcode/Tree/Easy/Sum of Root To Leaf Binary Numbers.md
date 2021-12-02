### Question:
https://leetcode.com/problems/sum-of-root-to-leaf-binary-numbers/

### Algo:
dfs, bfs

### Sol(dfs)
```
class Solution {
    int sum = 0;
    public int sumRootToLeaf(TreeNode root) {
        preorder(root, 0);
        return sum;
    }
    
    public void preorder(TreeNode root, int currNumber) {
        if(root == null)
            return;
        
        currNumber = (currNumber << 1) | root.val; 
        
        if(root.left == null && root.right == null)
            sum += currNumber;
        
        preorder(root.left, currNumber);
        preorder(root.right, currNumber);
    }
}
```
### Sol(bfs)
```
class Solution {
    public int sumRootToLeaf(TreeNode root) {
        int rootToLeaf = 0, currNumber = 0;
        Deque<Pair<TreeNode, Integer>> stack = new ArrayDeque();
        stack.push(new Pair(root, 0));

        while (!stack.isEmpty()) {
          Pair<TreeNode, Integer> p = stack.pop();
          root = p.getKey();
          currNumber = p.getValue();

          if (root != null) {
            currNumber = (currNumber << 1) | root.val;
            // if it's a leaf, update root-to-leaf sum
            if (root.left == null && root.right == null) {
              rootToLeaf += currNumber;
            } else {
              stack.push(new Pair(root.right, currNumber));
              stack.push(new Pair(root.left, currNumber));
            }
          }
        }
        return rootToLeaf;
    }
}
```
