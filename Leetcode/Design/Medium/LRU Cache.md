### Question:
https://leetcode.com/problems/lru-cache/

### Algo:
DLL, HashMap

### Sol:
```
class Node {
    int key, data;
    Node prev, next;
    
    public Node(int key, int data) {
        this.key = key;
        this.data = data;
    }
}

class LRUCache {

    Node head, tail;
    Map<Integer, Node> nodeAddress;
    int capacity;
    
    public LRUCache(int capacity) {
        this.nodeAddress = new HashMap<>();
        this.capacity = capacity;
    }
    
    public int get(int key) {
        Node node = nodeAddress.get(key);
        if(node == null)
            return -1;
        
        moveNodeToFirstIndex(node);
        return node.data;
    }
    
    public void put(int key, int value) {
        
        Node newNode = nodeAddress.get(key);
        
        if(newNode != null) {
            deleteNode(newNode);
            newNode.data = value;
            nodeAddress.remove(key);
        } else {
           newNode = new Node(key, value);
        }
        
        if(capacity <= nodeAddress.size()) {
            nodeAddress.remove(tail.key);
            tail = tail.prev;
        }
        
        addNode(newNode);
        nodeAddress.put(key, newNode);
    }
    
    public void moveNodeToFirstIndex(Node node) {
        deleteNode(node);
        addNode(node);
    }
    
    public void addNode(Node node) {
        if(tail == null || head == null)
            head = tail = node;
        else {
            tail.next = null;
            node.next = head;
            head.prev = node;
            head = node;
        }
    }
    
    public void deleteNode(Node node) {
        if(head == tail)
            head = tail = null;
        else if(head == node) {
            head = head.next;
            head.prev.next = null;
            head.prev = null;
        } else if(node == tail) {
            tail = tail.prev;
            tail.next.prev = null;
            tail.next = null;
        } else {
            node.next.prev = node.prev;
            node.prev.next = node.next;
        }
        
        node.prev = node.next = null;
    }
}
```
