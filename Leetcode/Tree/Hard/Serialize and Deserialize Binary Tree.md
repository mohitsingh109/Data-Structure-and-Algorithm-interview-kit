### Question:
https://leetcode.com/problems/serialize-and-deserialize-binary-tree/

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
 *     TreeNode(int x) { val = x; }
 * }
 */
public class Codec {

    // Encodes a tree to a single string.
    public String serialize(TreeNode root) {
        
        if(root == null)
            return null;
        
        Queue<TreeNode> queue = new LinkedList<>();
        StringBuilder res = new StringBuilder();
        queue.add(root);
        
        while(!queue.isEmpty()) {
            TreeNode node = queue.remove();
            String val = "null";
            if(node != null)
                val = String.valueOf(node.val);
            
            if(res.isEmpty())
                res.append(val);
            else 
                res.append(",").append(val);
            
            if(node != null) {
                queue.add(node.left);
                queue.add(node.right);
            }
        }
        
        return res.toString();
    }

        // Decodes your encoded data to tree.
    public TreeNode deserialize(String data) {
        if(data == null)
            return null;
        
        String[] nodes = data.split(",");
        
        TreeNode root = new TreeNode(Integer.valueOf(nodes[0]));
        Queue<TreeNode> queue = new LinkedList<>();
        queue.add(root);
        
        for(int index = 1; index < nodes.length; index+=2) {
            TreeNode node = queue.remove();
            if(!nodes[index].equals("null")) {
                node.left = new TreeNode(Integer.valueOf(nodes[index]));
                queue.add(node.left);
            }
            
            if(index + 1 < nodes.length && !nodes[index + 1].equals("null")) {
                node.right = new TreeNode(Integer.valueOf(nodes[index + 1]));
                queue.add(node.right);
            }
        }
        
        return root;
    }
}

// Your Codec object will be instantiated and called as such:
// Codec ser = new Codec();
// Codec deser = new Codec();
// TreeNode ans = deser.deserialize(ser.serialize(root));

```
