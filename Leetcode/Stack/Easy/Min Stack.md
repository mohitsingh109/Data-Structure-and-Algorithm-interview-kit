### Question: 
https://leetcode.com/problems/min-stack/

### Algo:
Stack

### Sol: 
```
class MinStack {

    private Stack<Integer> stack;
    private Stack<Integer> minStack;
    
    public MinStack() {
        this.stack = new Stack();
        this.minStack = new Stack();
    }
    
    public void push(int val) {
        stack.push(val);
        if(minStack.isEmpty() || minStack.peek() >= val)
            minStack.push(val);
    }
    
    public void pop() {
        int value = stack.pop();
        if(minStack.peek() == value)
            minStack.pop();
    }
    
    public int top() {
        return stack.peek();
    }
    
    public int getMin() {
         return minStack.peek();
    }
}

/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack obj = new MinStack();
 * obj.push(val);
 * obj.pop();
 * int param_3 = obj.top();
 * int param_4 = obj.getMin();
 */
 ```
