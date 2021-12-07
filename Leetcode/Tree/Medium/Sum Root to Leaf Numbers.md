### Question:
https://leetcode.com/problems/sum-root-to-leaf-numbers/

### Algo:
Pre-order

### Sol:
```
class Solution {
    int total = 0;
    public int sumNumbers(TreeNode root) {
        leafSum(root, 0);
        return total;
    }
    
    public void leafSum(TreeNode node, int value) {
        if(node == null)
            return;
        
        value = value * 10 + node.val;
        if(node.left == null && node.right == null) {
            total += value;
            return;
        }
        
        leafSum(node.left, value);
        leafSum(node.right, value);
    }
}
```
