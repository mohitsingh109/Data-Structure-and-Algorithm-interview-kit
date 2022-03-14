### Question:
https://leetcode.com/problems/all-nodes-distance-k-in-binary-tree/


### Algo:
Hash Table

### Sol-1 (Hash table for child to parent link)
```
class Solution {
    List<Integer> result = new ArrayList<>();
    Set<TreeNode> visited = new HashSet<>();
    
    public List<Integer> distanceK(TreeNode root, TreeNode target, int k) {
        Map<TreeNode, TreeNode> parentLink = linkChildToParent(root);
        dfs(target, k, parentLink);
        return result;
    }
    
    public void dfs(TreeNode target, int k, Map<TreeNode, TreeNode> parentLink) {
        if(target == null)
            return;
        
        if(visited.contains(target))
            return;
        
        visited.add(target);
        
        if(k == 0) {
            result.add(target.val);
            return;
        }
        
        dfs(target.left, k - 1, parentLink);
        dfs(target.right, k - 1, parentLink);
        dfs(parentLink.get(target), k - 1, parentLink);
    }
    
    public Map<TreeNode, TreeNode> linkChildToParent(TreeNode root) {
        Queue<TreeNode> queue = new LinkedList<>();
        Map<TreeNode, TreeNode> parentLink = new HashMap<>();
        queue.add(root);
        
        while(!queue.isEmpty()) {
            TreeNode node = queue.remove();
            if(node.left != null) {
                parentLink.put(node.left, node);
                queue.add(node.left);
            }
            
            if(node.right != null) {
                parentLink.put(node.right, node);
                queue.add(node.right);
            }
        }
        
        return parentLink;
    }
}
```

### Sol-2(dfs)
```
class Solution {
    List<Integer> result = new ArrayList<>();
    
    public List<Integer> distanceK(TreeNode root, TreeNode target, int k) {
        kDistance(root, target, k);
        return result;
    }
    
    public int kDistance(TreeNode root, TreeNode target, int k) {
        if(root == null)
            return -1;
        
        if(root == target) {
            kNode(root, k);
            return 1;
        }
        
        int left = kDistance(root.left, target, k);
        if(left != -1) {
             if(k == left) result.add(root.val);
            kNode(root.right, k - (left + 1));
            return left + 1;
        }
        
        int right = kDistance(root.right, target, k);
         
        if(right != -1) {
            if(k == right) result.add(root.val);
            kNode(root.left, k - (right + 1));
            return right + 1;
        }
        
        return -1;
    }
    
    public void kNode(TreeNode root, int k) {
        
        if(root == null || k < 0)
            return;
        
        if(k == 0) {
            result.add(root.val);
            return;
        }
        
        kNode(root.left, k - 1);
        kNode(root.right, k - 1);
    }
}
```
