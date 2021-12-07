### Question:
https://leetcode.com/problems/pascals-triangle-ii/

### Algo:
Array

### Sol1:
```
class Solution {
     public List<Integer> getRow(int k) {
        Integer[] arr = new Integer[k + 1];
        Arrays.fill(arr, 0);
        arr[0] = 1;
        
        for (int i = 1; i <= k; i++) 
            for (int j = i; j > 0; j--) 
                arr[j] = arr[j] + arr[j - 1];
        
        return Arrays.asList(arr);
    }
}
```

### Sol2:
```
class Solution {
    public List<Integer> getRow(int rowIndex) {
        List<Integer> res = new ArrayList<>();
        List<Integer> prev = null;
        
        res.add(1);    
        
        for(int row = 1; row <=rowIndex; row++) {
            prev = res;
            res = new ArrayList<>();
            res.add(1);
            for(int i = 1; i < row; i++)
                res.add(prev.get(i-1) + prev.get(i));
            res.add(1);
        }
        
        return res;
    }
}
```
