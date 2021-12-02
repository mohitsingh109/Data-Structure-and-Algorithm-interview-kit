### Question:
https://leetcode.com/problems/jewels-and-stones/

### Algo:
Hash Table

### Sol:
```
class Solution {
    public int numJewelsInStones(String jewels, String stones) {
        int[] arr = new int[256];
        
        for(int i = 0; i < stones.length(); i++) {
            arr[stones.charAt(i)]++;
        }
        
        int count = 0;
        
        for(int i = 0; i < jewels.length(); i++) {
            count += arr[jewels.charAt(i)];
        }
        
        return count;
    }
}
```
