### Question:
https://leetcode.com/problems/last-stone-weight/

### Algo:
Max Heap

### Sol:
```
class Solution {
    public int lastStoneWeight(int[] stones) {
        PriorityQueue<Integer> pq = new PriorityQueue<>(Collections.reverseOrder());
        
        for(int val : stones)
            pq.add(val);
        
        while(pq.size() > 1) {
            int val1 = pq.remove();
            int val2 = pq.remove();
            
            if(val1 != val2)
                pq.add(val1-val2);
        }
        
        return pq.isEmpty()? 0: pq.peek();
    }
}
```
