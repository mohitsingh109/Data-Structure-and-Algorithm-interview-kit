### Question:
https://leetcode.com/problems/merge-k-sorted-lists/


### Algo:
Priority Queue

### Sol:
```
class Solution {
    public ListNode mergeKLists(ListNode[] lists) {
        
        if(lists == null || lists.length == 0)
            return null;
        
        PriorityQueue<ListNode> pq = new PriorityQueue<>((node1, node2) -> node1.val - node2.val);
        
        for(ListNode node: lists)
            if(node != null)
                pq.add(node);
        
        ListNode dummyNode = new ListNode();
        ListNode tailNode = dummyNode;
        
        while(!pq.isEmpty()) {
            ListNode node = pq.remove();
            if(node.next != null)
                pq.add(node.next);
            
            tailNode.next = node;
            tailNode = tailNode.next;
            tailNode.next = null;
        }
        
        return dummyNode.next;
    }
}
```
