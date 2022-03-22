### Question:
https://leetcode.com/problems/all-elements-in-two-binary-search-trees/

### Algo:
Inorder, Merge Sort List

### Sol:
```
class Solution {
    public List<Integer> getAllElements(TreeNode root1, TreeNode root2) {
        List<Integer> l1 = new ArrayList<>();
        List<Integer> l2 = new ArrayList<>();
        
        inOrder(root1, l1);
        inOrder(root2, l2);
        
        List<Integer> result = new ArrayList<>();
        
        int i1 = 0;
        int i2 = 0;
        
        while(i1 < l1.size() || i2 < l2.size()) {
            
            int val1 = i1 == l1.size()? Integer.MAX_VALUE: l1.get(i1);
            int val2 = i2 == l2.size()? Integer.MAX_VALUE: l2.get(i2);
            
            if(val1 < val2) {
                result.add(val1);
                i1++;
            } else {
                result.add(val2);
                i2++;
            }
        }
        
        return result;
    }
    
    
    public void inOrder(TreeNode root, List<Integer> list) {
        if(root == null)
            return;
        
        inOrder(root.left, list);
        list.add(root.val);
        inOrder(root.right, list);
    }
}
```
