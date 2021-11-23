### Question: 
https://leetcode.com/problems/linked-list-cycle/

### Algo:
Floyd's Cycle Detection Algorithm

### Ref:
https://www.youtube.com/watch?v=jcZtMh_jov0

### Sol:
```
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
 
public class Solution {
    public boolean hasCycle(ListNode head) {
     
        ListNode slow = head;
        ListNode fast = head;
        
        while(fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
            if(fast == slow)
                return true;   
        }
        
        return false;
    }
}
```
