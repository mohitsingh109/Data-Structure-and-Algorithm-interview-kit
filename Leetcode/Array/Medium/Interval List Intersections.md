### Question:
https://leetcode.com/problems/interval-list-intersections/

### Algo:
Array, Math, Two Pointer

### Sol:
```
class Solution {
    public int[][] intervalIntersection(int[][] firstList, int[][] secondList) {
        List<int []> res = new ArrayList<>();
        
        int i = 0, j = 0;
        while(i < firstList.length && j < secondList.length) {
            if(firstList[i][0] <= secondList[j][1] && secondList[j][0] <= firstList[i][1]) {
                res.add(new int[]{Math.max(firstList[i][0], secondList[j][0]), Math.min(firstList[i][1], secondList[j][1])});
            }
            
            if(secondList[j][1] > firstList[i][1])
                i++;
            else 
                j++;
        }
        
        return res.toArray(new int[0][]);
    }
}
```
