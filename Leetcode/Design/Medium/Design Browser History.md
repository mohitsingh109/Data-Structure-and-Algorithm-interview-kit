### Question:
https://leetcode.com/problems/design-browser-history/

### Algo:
Stack, DLL

### Sol(DDL)
```
class BrowserHistory {
    
    class Node {
        Node back;
        Node forward;
        String val;
        
        public Node(String val) {
            this.val = val;
        }
    }

    private Node currNode;
    
    public BrowserHistory(String homepage) {
       this.currNode = new Node(homepage);
    }
    
    public void visit(String url) {
        currNode.forward = new Node(url);
        currNode.forward.back = currNode;
        currNode = currNode.forward;
    }
    
    public String back(int steps) {
        while(steps > 0 && currNode.back != null) {
            currNode = currNode.back;
            steps--;
        }
        
        return currNode.val;
    }
    
    public String forward(int steps) {
    
        while(steps > 0 && currNode.forward != null) {
            currNode = currNode.forward;
            steps--;
        }
        
        return currNode.val;
    }
}

/**
 * Your BrowserHistory object will be instantiated and called as such:
 * BrowserHistory obj = new BrowserHistory(homepage);
 * obj.visit(url);
 * String param_2 = obj.back(steps);
 * String param_3 = obj.forward(steps);
 */
```

### Sol-2(Stack)
```
class BrowserHistory {

    private final Stack<String> backStack;
    private final Stack<String> forwardStack;
    
    public BrowserHistory(String homepage) {
        this.backStack = new Stack<>();
        this.forwardStack = new Stack<>();
        visit(homepage);
    }
    
    public void visit(String url) {
        backStack.push(url);
        forwardStack.clear();
    }
    
    public String back(int steps) {
        while(steps > 0 && backStack.size() > 1) {
            forwardStack.push(backStack.pop());
            steps--;
        }
        
        return backStack.peek();
    }
    
    public String forward(int steps) {
    
        while(steps > 0 && !forwardStack.isEmpty()) {
            backStack.push(forwardStack.pop());
            steps--;
        }
        
        return backStack.peek();
    }
}

/**
 * Your BrowserHistory object will be instantiated and called as such:
 * BrowserHistory obj = new BrowserHistory(homepage);
 * obj.visit(url);
 * String param_2 = obj.back(steps);
 * String param_3 = obj.forward(steps);
 */
```
