### Question:
https://leetcode.com/problems/copy-list-with-random-pointer/

### Algo:
Linked List

### Sol:
```
class Solution {
    public Node copyRandomList(Node head) {
        Node pass = head;
        
        while(pass != null) {
            Node next = pass.next;
            pass.next = new Node(pass.val);
            pass.next.next = next;
            pass = next;
        }
        
        pass = head;
        
        while(pass != null) {
            pass.next.random = pass.random == null? null: pass.random.next;
            pass = pass.next.next;
        }
        
        pass = head;
        Node cloneHead = new Node(0);
        Node tail = cloneHead;
        while(pass != null) {
            Node next = pass.next;
            pass.next = next.next;
            tail.next = next;
            tail = tail.next;
            tail.next = null;
            pass = pass.next;
        }
        
        return cloneHead.next;
    }
}
```
