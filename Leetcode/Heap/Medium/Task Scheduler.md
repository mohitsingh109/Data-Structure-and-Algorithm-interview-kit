### Question:
https://leetcode.com/problems/task-scheduler/

### Algo:
Priority Queue, Hash Table

### Sol (With Queue):
```
class Solution {
    public int leastInterval(char[] tasks, int n) {
        int[] map = new int[26];
        int time = 0;
        
        for(char ch : tasks)
            map[ch - 'A']++;
        
        PriorityQueue<Integer> pq = new PriorityQueue<>((a, b) -> b - a);
        Queue<int[]> queue = new LinkedList<>();
        
        for(int value : map)
            if(value != 0)
                pq.add(value);
        
        while(!pq.isEmpty() || !queue.isEmpty()) {
            time++;
            
            if(!pq.isEmpty()) {
                int value = pq.remove() - 1;
                if(value != 0)
                    queue.add(new int[]{value, time + n});
            }
            
            if(!queue.isEmpty()) {
                int[] value = queue.peek();
                if(time >= value[1])
                    pq.add(queue.remove()[0]);
            }
        }
        
        return time;
    }
}
```

### Sol:
```
class Solution {
    public int leastInterval(char[] tasks, int n) {
        int[] map = new int[26];
        int res = 0;
        
        for(char ch : tasks)
            map[ch - 'A']++;
        
        PriorityQueue<Integer> pq = new PriorityQueue<>((a, b) -> b - a);
        
        for(int value: map)
            if(value != 0)
                pq.add(value);
            
        
        while(!pq.isEmpty()) {
           
            int time = 0;
            
            List<Integer> temp = new ArrayList<>(); 
            
            for(int i = 0; i <= n; i++) {
                 if(!pq.isEmpty()) {
                     temp.add(pq.remove() - 1);
                     time++;
                 }
            }
            
            for(int value: temp) {
                if(value != 0)
                    pq.add(value);
            }
            
            res += pq.isEmpty()? time: n + 1;
        }
        
        return res;
    }
}
```
