### Question:
https://leetcode.com/problems/132-pattern/

### Algo:
Tree Map, Stack

### Sol(Stack):
```
class Solution {
    public boolean find132pattern(int[] nums) {
        if(nums.length < 3)
            return false;
        
        int[] minValue = new int[nums.length];
        minValue[0] = nums[0];
        Stack<Integer> stack = new Stack<>();
        
        for(int i = 1; i < nums.length; i++)
            minValue[i] = Math.min(minValue[i - 1], nums[i]);
        
        for(int i = nums.length - 1; i >= 0; i--) {
            
            while(!stack.isEmpty() && stack.peek() <= minValue[i])
                    stack.pop();
            
            /*
             i = minValue[i] 
             k = stack.peek()
             j = nums[current value]
            */
            
            if(!stack.isEmpty() && stack.peek() < nums[i])
                return true;
            
            stack.push(nums[i]);
        }
        
        return false;
    }
}
```

### Sol(Tree Map)
```
class Solution {
    public boolean find132pattern(int[] nums) {
        int n = nums.length;
        
        // impossible
        if (n < 3) {
            return false;
        }
        
        // a self-balancing BST to keep track of numbers and their counts.
        TreeMap<Integer, Integer> t = new TreeMap();
        for (int i = 1; i < n; i++) {
            t.put(nums[i], t.getOrDefault(nums[i], 0) + 1);
        }
        
        int min_i = Integer.MAX_VALUE;
        for (int j = 1; j < n; j++) {
            min_i = Math.min(min_i, nums[j-1]);
            
            // exclude the current nums[j] from the search space
            // if the count is 0, simply discard the node from the BST.
            t.put(nums[j], t.get(nums[j]) - 1);
            if (t.get(nums[j]) == 0) {
                t.remove(nums[j]);
            }
            
            if (nums[j] < min_i) {
                continue;
            }
            
            // check if a number, nums[k], exists in the current search space
            // such that min_i < nums[k] < nums[j].
            if (t.subMap(min_i, false, nums[j], false).size() > 0) {
                return true;
            }
        }
        
        return false;
    }
}
```
