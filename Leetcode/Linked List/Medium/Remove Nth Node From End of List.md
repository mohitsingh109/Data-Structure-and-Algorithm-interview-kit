### Question:
https://leetcode.com/problems/remove-nth-node-from-end-of-list/

### Algo:
Linked List, Two pointer

### Sol:
```
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode dummyNode = new ListNode(0, head);
        ListNode fast, slow;
        fast = slow = dummyNode;
        for(int i = 1; i <= n + 1; i++)
            fast = fast.next;
        
        while(fast != null) {
            fast = fast.next;
            slow = slow.next;
        }
        
        slow.next = slow.next.next;
        
        return dummyNode.next;
    }
}
```
