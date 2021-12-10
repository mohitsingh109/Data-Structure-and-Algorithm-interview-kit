### Question:
https://leetcode.com/problems/add-two-numbers/

### Algo:
Linked List, Math

### Sol:
```
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode head = new ListNode(0), tail = head;
        int carry = 0;
        
        while(l1 != null || l2 != null || carry != 0) {
            
            int sum = (l1 != null? l1.val: 0) + (l2 != null? l2.val: 0) + carry;
            carry = sum/10;
            sum = sum % 10;
            tail.next = new ListNode(sum);;
            tail = tail.next;
            
            l1 = l1 != null? l1.next: l1;
            l2 = l2 != null? l2.next: l2;
        }
        
        return head.next;
    }
}
```
