### Question:
https://leetcode.com/problems/combination-sum/

### Algo:
dfs

### Sol:
```
class Solution {
    List<List<Integer>> result = new ArrayList<>();
    public List<List<Integer>> combinationSum(int[] candidates, int target) {
        backtrack(0, candidates, 0, target, new LinkedList<>());
        return result;
    }
    
    public void backtrack(int currentIndex, int[] candidates, int runningSum, int target, LinkedList<Integer> list) {
        
        if(runningSum == target) {
            result.add(new ArrayList<>(list));
            return;
        }
        
        if(runningSum > target || currentIndex == candidates.length)
            return;
        
        list.add(candidates[currentIndex]);
        backtrack(currentIndex, candidates, runningSum + candidates[currentIndex], target, list);
        
        list.removeLast();
        backtrack(currentIndex + 1, candidates, runningSum , target, list);
            
    }
}
```

### Reference:
- https://www.youtube.com/watch?v=GBKI9VSKdGg
