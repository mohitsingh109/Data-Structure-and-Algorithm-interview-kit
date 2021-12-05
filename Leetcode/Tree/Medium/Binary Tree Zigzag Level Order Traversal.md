### Question:
https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/

### Algo:
bfs, dfs

### Sol(bfs):
```
class Solution {
    public List<List<Integer>> zigzagLevelOrder(TreeNode root) {
        if(root == null)
            return Collections.emptyList();
        
        Stack<TreeNode> s1 = new Stack<>();
        Stack<TreeNode> s2 = new Stack<>();
        List<List<Integer>> traversal = new ArrayList<>();
        boolean flag = true;
        
        s1.push(root);
        while(!s1.isEmpty()) {
            int count = s1.size();
            List<Integer> values = new ArrayList<>(count);
            for(int i = 0; i < count; i++) {
                TreeNode node = s1.pop();
                values.add(node.val);
                if(flag) {
                    pushToStack(node.left, s2);
                    pushToStack(node.right, s2);
                } else {
                    pushToStack(node.right, s2);
                    pushToStack(node.left, s2);
                }
            }
            
            traversal.add(values);
            flag = !flag;
            
            Stack<TreeNode> temp = s1;
            s1 = s2;
            s2 = temp;
        }
        
        return traversal;
    }
    
    private void pushToStack(TreeNode node, Stack<TreeNode> st) {
        if(node == null) return;
        st.push(node);
    }
}
```

### Sol(dfs):
```
public List<List<Integer>> zigzagLevelOrder2(TreeNode root) {
     List<List<Integer>> ret = new ArrayList<>();
     dfs(root, 0, ret);
     return ret;
 }
 
 private void dfs(TreeNode node, int level, List<List<Integer>> ret) {
     if (node != null) {
         if (level == ret.size()) {
             List<Integer> list = new ArrayList<>();
             ret.add(list);
         }
         if (level % 2 == 1) {
            ret.get(level).add(0, node.val);  // insert at the beginning
         } else {
            ret.get(level).add(node.val);
         }
         dfs(node.left, level + 1, ret);
         dfs(node.right, level + 1, ret);
     }
 }
```
