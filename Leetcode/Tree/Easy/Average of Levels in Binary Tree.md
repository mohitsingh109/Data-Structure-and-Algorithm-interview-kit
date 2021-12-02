### Question:
https://leetcode.com/problems/average-of-levels-in-binary-tree/

### Algo:
bfs, dfs

### Sol(bfs):
```
class Solution {
    public List<Double> averageOfLevels(TreeNode root) {
        
        List<Double> res = new ArrayList<>();
        Queue<TreeNode> queue = new LinkedList<>();
        queue.add(root);
        
        while(!queue.isEmpty()) {
            int count = queue.size();
            long sum = 0;
            for(int i = 0; i < count; i++) {
                TreeNode node = queue.remove();
                sum += node.val;
                addNodeToQueue(node.left, queue);
                addNodeToQueue(node.right, queue);
            }
            
            res.add(sum * 1.0 / count);
        }
        
        return res;
    }
    
    public void addNodeToQueue(TreeNode root, Queue<TreeNode> queue) {
        if(root == null)
            return;
        
        queue.add(root);
    }
}
```

### Sol(dfs)
```
public class Solution {
    public List < Double > averageOfLevels(TreeNode root) {
        List < Integer > count = new ArrayList < > ();
        List < Double > res = new ArrayList < > ();
        average(root, 0, res, count);
        for (int i = 0; i < res.size(); i++)
            res.set(i, res.get(i) / count.get(i));
        return res;
    }
    public void average(TreeNode t, int i, List < Double > sum, List < Integer > count) {
        if (t == null)
            return;
        if (i < sum.size()) {
            sum.set(i, sum.get(i) + t.val);
            count.set(i, count.get(i) + 1);
        } else {
            sum.add(1.0 * t.val);
            count.add(1);
        }
        average(t.left, i + 1, sum, count);
        average(t.right, i + 1, sum, count);
    }
}
```
