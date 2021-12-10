### Question:
https://leetcode.com/problems/subsets/

### Algo:
Math, Bit Manipulation

### Sol:
```
class Solution {
    List<List<Integer>> ans = new ArrayList<>();
    public List<List<Integer>> subsets(int[] nums) {
        ans.add(Collections.emptyList());
        generateSubsets(nums, new LinkedList<>(), 0);
        return ans;
    }
    
    public void generateSubsets(int[] nums, LinkedList<Integer> subset, int index) {
        if(index == nums.length)
            return;
        
        subset.add(nums[index]);
        ans.add(new ArrayList<>(subset));
        generateSubsets(nums, subset, index + 1);
        subset.removeLast();
        generateSubsets(nums, subset, index + 1);
    }
    
}
```

### Sol(Bit Masking)
```

```
