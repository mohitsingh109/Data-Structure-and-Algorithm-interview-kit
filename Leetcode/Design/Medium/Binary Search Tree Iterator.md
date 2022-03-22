### Question:
https://leetcode.com/problems/binary-search-tree-iterator/

### Algo:
Tree

### Sol:
```
class BSTIterator {
    
    private final Stack<TreeNode> stack;
    private TreeNode root;

    public BSTIterator(TreeNode root) {
        this.root = root;
        this.stack = new Stack<>();
    }
    
    public int next() {
    
        while(root != null) {
            stack.push(root);
            root = root.left;
        }
        
        root = stack.pop();
        int val = root.val;
        root = root.right;
        return val;
    }
    
    public boolean hasNext() {
        return (root != null || !stack.isEmpty());
    }
}
```
