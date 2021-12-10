### Question:
https://leetcode.com/problems/permutations/

### Algo:
Math

### Sol:
```
class Solution {
    List<List<Integer>> allPermutation = new ArrayList<>();
    public List<List<Integer>> permute(int[] nums) {
        generatePermute(nums, 0, new LinkedList<>(), new boolean[nums.length]);
        return allPermutation;
    }
    
    public void generatePermute(int[] nums, int index, LinkedList<Integer> permutation, boolean[] used) {
        if(index == nums.length) {
            allPermutation.add(new ArrayList<>(permutation));
            return;
        }
        
        for(int start = 0; start < nums.length; start++) {
            if(used[start] == true) continue;
            used[start] = true;
            permutation.add(nums[start]);
            generatePermute(nums, index + 1, permutation, used);
            permutation.removeLast();
            used[start] = false;
        }
    }
}
```
