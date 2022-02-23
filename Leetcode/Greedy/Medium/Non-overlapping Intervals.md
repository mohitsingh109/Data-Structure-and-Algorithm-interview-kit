### Question:
https://leetcode.com/problems/non-overlapping-intervals/

### Algo:
Sort

### Sol:
```
class Solution {
    public int eraseOverlapIntervals(int[][] intervals) {
        
        Arrays.sort(intervals, (t1, t2) -> Integer.compare(t1[0], t2[0]));
        
        int minCount = 0;
        int endInterval = intervals[0][1];
        
        for(int i = 1; i < intervals.length; i++) {
            if(endInterval > intervals[i][0]) {
                endInterval = Math.min(endInterval, intervals[i][1]);
                minCount++;
            }else {
                endInterval = intervals[i][1];
            }
        }
        
        return minCount;
    }
}
```
