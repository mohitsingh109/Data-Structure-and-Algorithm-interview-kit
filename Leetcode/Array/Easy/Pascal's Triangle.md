### Question:
https://leetcode.com/problems/pascals-triangle/

### Algo:
Array

### Sol:
```
class Solution {
    public List<List<Integer>> generate(int numRows) {
        List<List<Integer>> res = new ArrayList<>();
        if(numRows >= 1)
            res.add(Arrays.asList(1));
        
        if(numRows >= 2)
            res.add(Arrays.asList(1,1));
            
        for(int row = 2; row < numRows; row++) {
            List<Integer> list = new ArrayList<>();
            List<Integer> prev = res.get(row - 1);
            list.add(1);
            for(int i = 1; i < row; i++)
                list.add(prev.get(i-1) + prev.get(i));
            list.add(1);
            res.add(list);    
        }
        
        return res;
    }
}
```
