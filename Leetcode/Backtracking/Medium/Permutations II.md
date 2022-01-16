### Question:
https://leetcode.com/problems/permutations-ii/

### Algo:
Hash Map

### Sol:
```
class Solution {
    List<List<Integer>> res = new ArrayList<>();
    public List<List<Integer>> permuteUnique(int[] nums) {
        Map<Integer, Integer> map = new HashMap<>();
        
        for(int val: nums)
            map.put(val, map.getOrDefault(val, 0) + 1);
        
        backtrack(map, new LinkedList<>(), nums.length);
        return res;
    }
    
    
    public void backtrack(Map<Integer, Integer> map, LinkedList<Integer> list, int len) {
        if(list.size() == len) {
            res.add(new ArrayList<>(list));
            return;
        }
        
        for(Integer key: map.keySet()) {
            if(map.get(key) == 0) continue;
            list.add(key);
            map.put(key, map.get(key) - 1);
            backtrack(map, list, len);
            list.removeLast();
            map.put(key, map.get(key) + 1);
        }
    }
}
```
