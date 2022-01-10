### Question:
https://leetcode.com/problems/find-the-duplicate-number/

### Algo:
Linked List Cycle

### Sol:
```
class Solution {
    public int findDuplicate(int[] nums) {
        int slow = nums[0];
        int fast = nums[0];
        
        do{
            slow = nums[slow];
            fast = nums[nums[fast]];
        } while(slow != fast);
        
        fast = nums[0];
        
        while(fast != slow) {
            slow = nums[slow];
            fast = nums[fast];
        }
        
        return slow;
    }
}
```

### Ref:
https://www.youtube.com/watch?v=wjYnzkAhcNk
