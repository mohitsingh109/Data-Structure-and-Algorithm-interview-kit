### Question:
https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons/

### Algo:
Sort

### Sol:
```
class Solution {
    public int findMinArrowShots(int[][] points) {
        Arrays.sort(points, (t1, t2) -> Integer.compare(t1[1], t2[1]));
        
        int count = 1;
        int end = points[0][1];
        
        for(int i = 1; i < points.length; i++) {
            if(end < points[i][0]) {
                count++;
                end = points[i][1];
            }
        }
        
        return count;
    }
}
```
