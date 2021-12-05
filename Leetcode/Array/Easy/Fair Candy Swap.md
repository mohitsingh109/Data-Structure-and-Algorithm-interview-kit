### Question:
https://leetcode.com/problems/fair-candy-swap/

### Algo:
Hash Set, Math

### Sol:
```
class Solution {
    public int[] fairCandySwap(int[] aliceSizes, int[] bobSizes) {
        Set<Integer> set = new HashSet<>();
        int totalA = 0, totalB = 0;
        int result[] = new int[2];
        
        for(int val : aliceSizes)
            totalA+=val;
        for(int val : bobSizes) {
            totalB+=val;
            set.add(val);
        }
        
        int delta = (totalB - totalA)/2;
        
        for(int val : aliceSizes) {
            if(set.contains(delta + val)) {
                result[0] = val;
                result[1] = delta + val;
                break;
            }
        }
        
        return result;
    }
}


/*
Formula:
A + x - y = B + y - x
x = (B - A)/2 + y
*/

```
