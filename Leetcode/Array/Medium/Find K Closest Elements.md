### Question:
https://leetcode.com/problems/find-k-closest-elements/

### Algo:
Binary Search, Sliding Window

### Sol(Binary Search):
```
  class Solution {
    public List<Integer> findClosestElements(int[] arr, int k, int x) {
        LinkedList<Integer> res = new LinkedList<>();
        int index = nearestElement(arr, x);
        int left = index - 1;
        int right = index;
        
        while(k-- > 0) {
            if(right >= arr.length || left >= 0 && ((x - arr[left]) <= (arr[right] - x))) {
                res.addFirst(arr[left--]);
            }else {
                res.addLast(arr[right++]);
            }
        }
        
        return res;
    }
    
    
    public int nearestElement(int[] arr, int x) {
        int left = 0;
        int right = arr.length - 1;
        
        while(left < right) {
            int mid = (left + right)/2;
            
            if(arr[mid] == x)
                return mid;
            
            if(arr[mid] > x)
                right = mid;
            else 
                left = mid + 1;
        }
        
        
        return left;
    }
}
```

### Sol:(Binary Search, Sliding Window)
```
class Solution {
    public List<Integer> findClosestElements(int[] arr, int k, int x) {
        List<Integer> res = new ArrayList<>();
        int left = 0;
        int right = arr.length - k;
        
        while(left < right) {
            int mid = (left + right)/2;
            
            if(x - arr[mid] > arr[mid + k] - x)
                left = mid + 1;
            else 
                right = mid;
        }
        
        while(k-- > 0)
            res.add(arr[left++]);
        
        return res;
    }
}

```

### Reference:
- https://www.youtube.com/watch?v=o-YDQzHoaKM
