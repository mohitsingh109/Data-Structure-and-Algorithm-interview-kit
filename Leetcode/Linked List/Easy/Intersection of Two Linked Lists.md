### Question:
https://leetcode.com/problems/intersection-of-two-linked-lists/

### Algo:
1. With space using Hash Set.
2. Without space
   - calculate length of both linked list.
   - we can travle d = abs(d1-d2) distance so both the linked list will become same length.
   - traverse both the list where ever it meet return the node.
   
   

### Sol-1:
```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        Set<ListNode> nodeAddress = new HashSet<>();
        
        while(headA != null) {
            nodeAddress.add(headA);
            headA = headA.next;
        }
        
        while(headB != null) {
            if(nodeAddress.contains(headB))
                return headB;
            headB = headB.next;
        }
        
        return null;
    }
}
```

### Sol-2:
```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        int d1 = 0;
        int d2 = 0;
        
        ListNode list1 = headA;
        ListNode list2 = headB;
        
        while(list1 != null) {
            d1++;
            list1 = list1.next;
        }
        
        while(list2 != null) {
            d2++;
            list2 = list2.next;
        }
        
        int distance = Math.abs(d1 - d2);
        if(d1 > d2)
            headA = travelNodeByXDistance(headA, distance);
        else
            headB = travelNodeByXDistance(headB, distance);
        
        while(headA != null && headB != null) {
            if(headA == headB)
                return headA;
            
            headA = headA.next;
            headB = headB.next;
        }
        
        return null;
    }
    
    public static ListNode travelNodeByXDistance(ListNode node, int distance) {
        while(distance > 0 && node != null) {
            node = node.next;
            distance--;
        }
        
        return node;
    }
}
```
