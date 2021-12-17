### Question:
https://leetcode.com/problems/longest-consecutive-sequence/

### Algo:
Hash Set

### Sol:
```
class Solution {
    public int longestConsecutive(int[] nums) {
        Set<Integer> set = new HashSet<>();
        int maxSequence = 0;
        
        for(int val : nums)
            set.add(val);
        
        for(int val : set) {
            if(set.contains(val - 1))
                continue;
            
            int currentlen = 1;
            while(set.contains(++val))
                currentlen++;
            
            maxSequence = Math.max(maxSequence, currentlen);
        }
        
        return maxSequence;
    }
}
```
