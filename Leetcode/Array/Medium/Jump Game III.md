### Question:
https://leetcode.com/problems/jump-game-iii/

### Algo:
dfs, bfs

### Sol (dfs):
```
class Solution {
    public boolean canReach(int[] arr, int start) {
        if(start >= arr.length || start < 0 || arr[start] == -1)
            return false;

        int val = arr[start];
        
        if(val == 0)
            return true;

        arr[start] = -1;

        return canReach(arr, start + val) || canReach(arr, start - val);
    }
}
```

### Sol(bfs)
```
class Solution {
    public boolean canReach(int[] arr, int start) {
        Queue<Integer> queue = new LinkedList<>();
        queue.add(start);
        
        while(!queue.isEmpty()) {
            int index = queue.remove();
            
            if(index < 0 || index >= arr.length)
                continue;
            
            if(arr[index] == 0)
                return true;
            
            if(arr[index] < 0)
                continue;
            
            arr[index] = -arr[index];
            
            queue.add(index + arr[index]);
            queue.add(index - arr[index]);
        }

        return false;
    }
}
```
