### Question:
https://leetcode.com/problems/largest-number/

### Algo:
Math, Sort

### Sol:
```
public class Solution {
    public String largestNumber(int[] nums) {
        if (nums == null || nums.length == 0) 
            return "";
        
        String[] strs = new String[nums.length];
        
        for (int i = 0; i < nums.length; i++) {
            strs[i] = String.valueOf(nums[i]);
        }
        
        Arrays.sort(strs, new Comparator<String>() {
            @Override
            public int compare(String i, String j) {
                String s1 = i+j;
                String s2 = j+i;
                return s2.compareTo(s1);
            }
        });
        
        if (strs[0].charAt(0) == '0') 
            return "0";
        
        StringBuilder sb = new StringBuilder();
        for (int i = 0; i < strs.length; i++) {
            sb.append(strs[i]);
        }
        return sb.toString();
    }
}
```
