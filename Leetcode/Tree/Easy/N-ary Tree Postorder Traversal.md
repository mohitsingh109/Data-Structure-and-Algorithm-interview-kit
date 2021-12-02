### Question
https://leetcode.com/problems/n-ary-tree-postorder-traversal/

### Algo
dfs

### Sol
```
/*
// Definition for a Node.
class Node {
    public int val;
    public List<Node> children;

    public Node() {}

    public Node(int _val) {
        val = _val;
    }

    public Node(int _val, List<Node> _children) {
        val = _val;
        children = _children;
    }
};
*/

class Solution {
    public List<Integer> postorder(Node root) {
        List<Integer> list = new ArrayList<>();
        postorderNArrayTree(root, list);
        return list;
    }
    
     public void postorderNArrayTree(Node root, List<Integer> list) {
         if(root == null)
             return;
         
         for(Node child: root.children) 
             postorderNArrayTree(child, list);
         
         list.add(root.val);
     }
}
```
