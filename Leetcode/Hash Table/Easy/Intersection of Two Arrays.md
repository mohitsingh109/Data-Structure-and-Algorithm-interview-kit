### Question:
https://leetcode.com/problems/intersection-of-two-arrays-ii/

### Algo:
Hash Map

### Sol:

```
class Solution {
    public int[] intersect(int[] nums1, int[] nums2) {
        Map<Integer, Integer> map = new HashMap<>();
        
        for(int val : nums1)
            map.put(val, map.getOrDefault(val, 0) + 1);
            
        List<Integer> result = new ArrayList<>();
        for(int val: nums2){
            if(map.containsKey(val) && map.get(val) > 0) {
                result.add(val);
                map.put(val, map.get(val) - 1);
            }
        }
        
        return result.stream().mapToInt(Integer::intValue).toArray();
    }
}


// Arrays.copyOfRange(nums1, start_index, number_of_element);
```
