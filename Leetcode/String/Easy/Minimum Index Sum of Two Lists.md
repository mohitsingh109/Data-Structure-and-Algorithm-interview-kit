### Question:
https://leetcode.com/problems/minimum-index-sum-of-two-lists/

### Algo:
Hash Map, Priority Queue

### Sol1 (Priority Queue)
```
class Solution {
    class IndexSumInfo {
        int sum;
        String val;
        
        public IndexSumInfo(int sum, String val) {
            this.sum = sum;
            this.val = val;
        }
    }
    public String[] findRestaurant(String[] list1, String[] list2) {
        PriorityQueue<IndexSumInfo> pq = new PriorityQueue<>((i1, i2) -> i1.sum - i2.sum);
        Map<String, Integer> map = new HashMap<>();
        
        for(int i = 0; i < list1.length; i++)
            map.put(list1[i], i);
        
        for(int i = 0; i < list2.length; i++){
            int index = map.getOrDefault(list2[i], -1);
            if(index != -1) {
                pq.add(new IndexSumInfo(index + i, list2[i]));
            }
        }
        
        List<String> list = new ArrayList<>();
        IndexSumInfo info = null;
        while(!pq.isEmpty()) {
            if(info == null)
                info = pq.peek();
            else if(info.sum != pq.peek().sum)
                break;
            
            list.add(pq.remove().val);
        }
        
        return list.toArray(new String[1]);
    }
}
```

### Sol2:
```
class Solution {
    public String[] findRestaurant(String[] list1, String[] list2) {
        Map<String, Integer> map = new HashMap<>();
        List<String> list = null;
        int minSum = Integer.MAX_VALUE;
        
        for(int i = 0; i < list1.length; i++)
            map.put(list1[i], i);
        
        for(int i = 0; i < list2.length; i++) {
            int index = map.getOrDefault(list2[i], -1);
            if(index != -1) {
                if(minSum > index + i) {
                    list = new ArrayList<>();
                    list.add(list2[i]);
                    minSum = index + i;
                } else if(minSum == index + i) {
                    list.add(list2[i]);
                }
            }
        }
        
        return list.toArray(new String[1]);
    }
}
```
