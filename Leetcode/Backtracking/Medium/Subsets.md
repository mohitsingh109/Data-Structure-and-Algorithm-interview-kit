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
### Sol(iterative):
```
class Solution {
    public List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>> ans = new ArrayList<>();
        ans.add(new ArrayList<>());
        
        for(int n: nums) {
            int count = ans.size();
            for(int i = 0; i< count; i++) {
                List<Integer> subset = new ArrayList<>(ans.get(i));
                subset.add(n);
                ans.add(subset);
            }
        }
        return ans;
    }    
}
```

### Sol(Bit Masking)
```
class Solution {
    public List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>> ans=  new ArrayList<>();
        
        for(int i = 0; i < (1 << nums.length); ++i) {
            List<Integer> res = new ArrayList<>();
            for(int j= 0; j < nums.length; ++j) {
                if(((i >> j) & 1 ) != 0)
                    res.add(nums[j]);
            }
            ans.add(new ArrayList(res));
        }
        
        return ans;
    }    
}
```
