### Question:
https://leetcode.com/problems/daily-temperatures/

### Algo:
Monotonic Stack

### Sol:
```
class Solution {
    public int[] dailyTemperatures(int[] temperatures) {
        
        int len  = temperatures.length;
        int[] result = new int[len];
        Stack<Integer> stack = new Stack<>();
        
        for(int i = 0; i < len; i++) {
            while(!stack.isEmpty() && temperatures[i] > temperatures[stack.peek()]) {
                int idx = stack.pop();
                result[idx] = i - idx;
            }
            
            stack.push(i);
        }
        
        return result;
    }
}
```
