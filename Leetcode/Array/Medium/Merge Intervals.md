### Question:
https://leetcode.com/problems/merge-intervals/

### Algo:
Math, Sort

### Sol:
```
class Solution {
    public int[][] merge(int[][] intervals) {
        Arrays.sort(intervals, (a, b) -> Integer.compare(a[0], b[0]));
        
        List<int []> res = new ArrayList<>(){{
            add(new int[] {intervals[0][0], intervals[0][1]});
        }};
        
        for(int i = 1; i < intervals.length; i++) {
            int index = res.size() - 1;
            int[] pair = res.get(index);
            
            if(intervals[i][0] > pair[1]) {
                res.add(intervals[i]);
            } else {
                pair[1] = Math.max(pair[1], intervals[i][1]);
            }
        }
        
        return res.toArray(new int[0][]);
    }
}
```
