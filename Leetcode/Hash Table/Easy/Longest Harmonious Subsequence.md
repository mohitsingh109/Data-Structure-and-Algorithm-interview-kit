### Question:
https://leetcode.com/problems/longest-harmonious-subsequence/

### Algo:
Hash Table

### Sol:
```
class Solution {
    public int findLHS(int[] nums) {
        Map<Integer, Integer> table = new HashMap<>();
        
        for(int num: nums)
            table.put(num, table.getOrDefault(num, 0) + 1);
        
        int count = 0;

        for(Integer key: table.keySet())
            if(table.containsKey(key + 1))
                count = Math.max(count, table.get(key + 1) + table.get(key));
        
        return count;
    }
}
```
