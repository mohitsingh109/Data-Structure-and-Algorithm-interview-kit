### Question:
https://leetcode.com/problems/the-k-weakest-rows-in-a-matrix/

### Algo:
Max Heap, Binary Search, Matrix

### Sol:
```
class Solution {
    class RowInfo {
        int row;
        int soldiers;
        
        public RowInfo(int row, int soldiers) {
            this.row = row;
            this.soldiers = soldiers;
        }
    }
    
    public int[] kWeakestRows(int[][] mat, int k) {
        PriorityQueue<RowInfo> pq = new PriorityQueue<>((r1, r2) -> {
            return r2.soldiers != r1.soldiers? r2.soldiers - r1.soldiers: r2.row-r1.row;
        });
        
        for(int row = 0 ; row < mat.length; row++) {
            pq.add(new RowInfo(row, count(mat[row])));
            
            if(pq.size() > k)
                pq.remove();
        }
        
        int[] arr = new int[k];
        int idx = k - 1;
        while(!pq.isEmpty()){
            arr[idx--] = pq.remove().row;
        }
        
        return arr;
    }
    
    public int count(int []arr){
        int low = 0,high = arr.length,mid = 0;
        while(low < high){
            mid = (low + (high - low)/2);
            if(arr[mid] == 1)low = mid + 1;
            else high = mid;
        }
        return low;
    }
}
```
