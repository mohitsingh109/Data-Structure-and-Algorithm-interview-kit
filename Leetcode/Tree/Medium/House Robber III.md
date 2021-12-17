### Question:
https://leetcode.com/problems/house-robber-iii/

### Algo:
DP

### Sol-1 (DP):
```
class Solution {
    Map<TreeNode, Integer> map = new HashMap<>();
    public int rob(TreeNode root) {
      if(root == null)
          return 0;
        
        if(map.containsKey(root)) 
            return map.get(root);
        
        int val = 0;
        if(root.left != null)
            val += rob(root.left.left) + rob(root.left.right);
        if(root.right !=null)
            val += rob(root.right.left) + rob(root.right.right);
        
        int maxMoney = Math.max(root.val + val, rob(root.left) + rob(root.right));
        map.put(root, maxMoney);
        return maxMoney;
    }
}
```

### Sol-2
```
class Solution {
   
    public int rob(TreeNode root) {
        int[] res = dfs(root);
        return Math.max(res[0], res[1]);
    }
    
    public int[] dfs(TreeNode root) {
      if(root == null)
          return new int[]{0, 0};
    
        int[] left = dfs(root.left);
        int[] right = dfs(root.right);
        
        int withRoot = root.val + left[1] + right[1];
        int withoutRoot = Math.max(left[0], left[1]) + Math.max(right[0], right[1]);
        
        return new int[]{withRoot, withoutRoot};
    }
}
```
