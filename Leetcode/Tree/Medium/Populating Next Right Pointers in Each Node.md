### Question:
https://leetcode.com/problems/populating-next-right-pointers-in-each-node/

### Algo:
dfs, bfs

### Sol:
```
ref: https://leetcode.com/problems/populating-next-right-pointers-in-each-node/discuss/962728/Java-0ms-with-visual-explanation

class Solution {
    public Node connect(Node root) {
        if(root == null) return null;
        if(root.left != null) root.left.next = root.right;
        if(root.right != null && root.next != null) root.right.next = root.next.left;
        connect(root.left);
        connect(root.right);
        return root;
    }
}
```

### Sol(bfs):
```
class Solution {
    public Node connect(Node root) {
        if(root == null)
            return null;
        
        Queue<Node> q = new LinkedList<>();
        q.add(root);
        
        while(!q.isEmpty()) {
            int count = q.size();
            for(int c = 0; c < count; c++) {
                 Node n = q.remove();
                 if(n.left != null)
                    q.offer(n.left);
                if(n.right != null)
                    q.offer(n.right);
                if(count - 1 != c)
                    n.next = q.peek();
            }
        }
        
        return root;
    }
}
```
