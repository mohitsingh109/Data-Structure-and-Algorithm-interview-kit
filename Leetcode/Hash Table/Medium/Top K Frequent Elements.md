### Question:
https://leetcode.com/problems/top-k-frequent-elements/

### Algo:
Hash Table, Priority Queue

### Sol1:
```
public class Solution {
    public int[] topKFrequent(int[] nums, int k) {
        Map<Integer, Integer> map = new HashMap<>();
        for(int n: nums)
            map.put(n, map.getOrDefault(n,0) + 1);
        
        // corner case: if there is only one number in nums, we need the bucket has index 1.
        List<Integer> [] bucket = new List[nums.length + 1];
        
        for(int key:map.keySet()) {
            int freq = map.get(key);
            
            if(bucket[freq] == null)
                bucket[freq] = new LinkedList<>();
            
            bucket[freq].add(key);
        }
        
        List<Integer> res = new LinkedList<>();
        
        for(int i = bucket.length - 1; i > 0 && k > 0; --i) {
            
            if(bucket[i] != null) {
                List<Integer> list = bucket[i]; 
                res.addAll(list);
                k -= list.size();
            }
        }
        
        return res.stream().mapToInt(i->i).toArray();
    }
}
```

### Sol2:
```
class Solution {
    public int[] topKFrequent(int[] nums, int k) {
        PriorityQueue<int[]> pq = new PriorityQueue<>((int[] a, int[] b) -> {
            return a[1] - b[1];
        });
        
        Map<Integer, Integer> map = new HashMap<>();
        for(int val: nums)
            map.put(val, map.getOrDefault(val, 0) + 1);
        
        for(Integer key: map.keySet()) {
            pq.add(new int[]{key, map.get(key)});
            
            if(pq.size() > k)
                pq.remove();
        }
        
        int[] res = new int[pq.size()];
        int i = 0;
        while(!pq.isEmpty()) {
            res[i++] = pq.poll()[0];
        }
        
        return res;
    }
}
```
