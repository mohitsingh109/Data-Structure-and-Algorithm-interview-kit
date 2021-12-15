### Question:
https://leetcode.com/problems/path-sum-iii/

### Algo:
dfs, prefix sum

### Sol(dfs - n * n):
```
class Solution {
    
    public int pathSum(TreeNode root, int targetSum) {
        if(root == null)
            return 0;
    
        return pathSum(root.left, targetSum) + pathSum(root.right, targetSum) + perNodedfs(root, targetSum);
    }
    
    public int perNodedfs(TreeNode root, int targetSum) {
       
         if(root == null)
            return 0;
        
         int res = 0; 
         if(root.val == targetSum)
            res++;
        
        res += perNodedfs(root.left, targetSum - root.val);
        res += perNodedfs(root.right, targetSum - root.val);
        return res;
    }
}
```

### Sol(prefix sum):
```
class Solution {
    int count = 0;
    Map<Integer, Integer> seen = new HashMap<>();
    
    public int pathSum(TreeNode root, int targetSum) {
        dfs(root, targetSum, 0);
        return count;
    }
    
    public void dfs(TreeNode root, int targetSum, int currentSum) {
       
        if(root == null)
          return;
        
        currentSum += root.val;
     
        if(currentSum == targetSum)
          count++;
        
        count += seen.getOrDefault((currentSum - targetSum), 0);
        seen.put(currentSum, seen.getOrDefault(currentSum, 0) + 1);
            
        dfs(root.left, targetSum, currentSum);
        dfs(root.right, targetSum, currentSum);
        
        if(seen.get(currentSum) != 0)
            seen.put(currentSum, seen.get(currentSum) - 1);
        
    }
}
```
