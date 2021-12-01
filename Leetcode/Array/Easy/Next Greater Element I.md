### Question:
https://leetcode.com/problems/next-greater-element-i/

### Algo:
Hash Map, Stack, Monotonic Stack

### Sol:
```
class Solution {
    public int[] nextGreaterElement(int[] nums1, int[] nums2) {
        Map<Integer, Integer> nextGreater = new HashMap<>();
        Stack<Integer> stack = new Stack<>();
        
        for(int val: nums2) {
            while(!stack.isEmpty() && stack.peek() < val) {
                nextGreater.put(stack.pop(), val);
            }
            
            stack.push(val);
        }
        
        for(int i = 0; i< nums1.length; i++){
            nums1[i] = nextGreater.getOrDefault(nums1[i], -1);
        }
        
        return nums1;
    }
}
```
