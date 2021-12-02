### Question:
https://leetcode.com/problems/destination-city/

### Algo:
Hash Set

### Sol:
```
class Solution {
    public String destCity(List<List<String>> paths) {
        Set<String> sourcePath = new HashSet<>();
        
        for(List<String> path: paths) {
            String sCity = path.get(0);
            sourcePath.add(sCity);
        }
        
        for(List<String> path: paths) {
            String dCity = path.get(1);
            if(!sourcePath.contains(dCity))
                return dCity;
        }
        
        return "";
    }
}
```
