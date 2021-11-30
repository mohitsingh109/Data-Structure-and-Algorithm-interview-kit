### Question:
https://www.interviewbit.com/old/problems/largest-number/

### Algo:
Sort(with custom comparator)

### Sol:
```
public class Solution {
    public String largestNumber(final List<Integer> A) {
        
        boolean allZero = true;
        for(int i =0; i < A.size(); i++){
            if(A.get(i) != 0) {
                allZero = false;
                break;
            }
        }
        
        if(allZero)
            return "0";
        
        Collections.sort(A, (Integer a, Integer b) -> {
            String s1 = String.valueOf(a) + String.valueOf(b);
            String s2 = String.valueOf(b) + String.valueOf(a);
            return s2.compareTo(s1);
        });

        StringBuilder sb = new StringBuilder();
        for(int i =0; i < A.size(); i++){
            sb.append(String.valueOf(A.get(i)));
        }

        return sb.toString();
    }
}

```
