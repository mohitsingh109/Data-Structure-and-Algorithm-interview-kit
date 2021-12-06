### Question:
https://leetcode.com/problems/kth-largest-element-in-an-array/

### Algo:
Priority Queue, Quick Select

### Sol(Priority Queue):
```
class Solution {
    public int findKthLargest(int[] nums, int k) {
        PriorityQueue<Integer> pq = new PriorityQueue<>();
        
        for(int val : nums) {
             pq.offer(val);
            if(pq.size() > k)
                pq.poll();
        }
        
        return pq.remove();
    }
}
```

### Sol(Quick Select):
```
class Solution {
    public int findKthLargest(int[] nums, int k) {
        return quickSelect(nums, 0 , nums.length - 1, nums.length - k);
    }
    
    public int quickSelect(int[] nums, int l, int r, int k) {
        int piviot = nums[r], p = l;
        
        for(int i = l; i < r; i++) {
            if(piviot >= nums[i]) {
                int temp = nums[i];
                nums[i] = nums[p];
                nums[p++] = temp;
            }
        }
        
        int temp = nums[p];
        nums[p] = nums[r];
        nums[r] = temp;
        
        if(k > p) return quickSelect(nums, p + 1, r, k);
        else if(k < p) return quickSelect(nums, l, p - 1, k);
        else return nums[p];
    }
}
```
