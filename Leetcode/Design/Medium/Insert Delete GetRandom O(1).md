### Question:
https://leetcode.com/problems/insert-delete-getrandom-o1/

### Algo:
Hash Map, Math

### Sol:
```
class RandomizedSet {
    Map<Integer, Integer> positions;
    List<Integer> data;
    Random random;

    public RandomizedSet() {
        this.positions = new HashMap<>();
        this.data = new ArrayList<>();
        this.random = new Random();
    }
    
    public boolean insert(int val) {
        boolean isPresent = isValueExist(val);
        if(!isPresent) {
            data.add(val);
            positions.put(val, data.size() - 1);
        }
        
        return !isPresent;
    }
    
    public boolean remove(int val) {
        boolean isPresent = isValueExist(val);
        if(isPresent) {
            int location = positions.get(val);
            int lastVal = data.get(data.size() - 1);
            data.set(location, lastVal);
            data.remove(data.size() - 1);
            positions.put(lastVal, location);
            positions.remove(val);
            
        }
        
        return isPresent;
    }
    
    public int getRandom() {
        return data.get(random.nextInt(data.size()));
    }
    
    public boolean isValueExist(int val) {
        return positions.containsKey(val);
    }
}
```
