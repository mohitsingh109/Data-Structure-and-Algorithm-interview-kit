### Question:
https://leetcode.com/problems/maximum-width-of-binary-tree/

### Algo:
Math(leftIndex = 2 * i +1, rightIndex = 2 * i + 2)

### Sol(pre-order)
```
class Solution {
    
    public int widthOfBinaryTree(TreeNode root) {
        Map<Integer, int[]> map = new HashMap<>();
        preorder(root, map, 0, 0);
        int maxWidth = 0;
        for(Integer key: map.keySet()) {
            int[] info = map.get(key);
            int nodeCount = info[1] - info[0] + 1;
            maxWidth = Math.max(maxWidth, nodeCount);
        }
        return maxWidth;
    }
 
    public void preorder(TreeNode root, Map<Integer, int[]> map, int level, int nodecount) {
        if(root == null)
            return;
        
        int[] info = map.getOrDefault(level, new int[]{nodecount, nodecount});
        info[1] = nodecount;
        map.putIfAbsent(level, info);
        preorder(root.left, map, level + 1, nodecount * 2 + 1);
        preorder(root.right, map, level + 1, nodecount * 2 + 2);
    }
}
```

### Sol(Level Order Traversal)
```
class Solution {
    class Pair {
        TreeNode node;
        int levelIndex;
        
        public Pair(TreeNode node, Integer levelIndex) {
            this.node = node;
            this.levelIndex = levelIndex;
        }
    }
    
    public int widthOfBinaryTree(TreeNode root) {
        int maxWidth = 0;
        Queue<Pair> q = new LinkedList<>();
        q.offer(new Pair(root, 0));
        while(!q.isEmpty()) {
            int minIndex = q.peek().levelIndex;
            int count = q.size();
            int first = 0, last = 0;
            for(int i = 0; i < count; i++) {
                Pair p = q.poll();
                int index = p.levelIndex - minIndex;
                TreeNode t = p.node;
                if(t.left != null)
                    q.offer(new Pair(t.left, 2 * index + 1));
                if(t.right != null)
                    q.offer(new Pair(t.right, 2 * index + 2));
                
                if(i == 0)
                    first = p.levelIndex;
                if(i == count - 1)
                    last = p.levelIndex;
            }
            maxWidth = Math.max(maxWidth, last - first + 1);
            
        }
        return maxWidth;
    }
}
```
