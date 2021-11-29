### Question:
https://www.interviewbit.com/problems/pick-from-both-sides/

### Algo:
Sliding Window, Prefix and Suffix Sums

### Sol-1 (Sliding Window)
```
public class Solution {
    public int solve(int[] A, int B) {

        Integer minVal = null;
        int currentSum = 0;
        int windowSize = A.length - B;
        int windowStart = 0;
        int total = 0;

        for(int windowEnd = 0; windowEnd < A.length; windowEnd++) {
            currentSum += A[windowEnd];
            total += A[windowEnd];
            if((windowEnd - windowStart + 1) == windowSize) {
                if(minVal == null || minVal > currentSum)
                    minVal = currentSum;
                
                currentSum-= A[windowStart++];
            }
        }

        return (total - (minVal == null? 0: minVal));
    }
}

```

### Sol-2 (Prefix and Suffix Sums)
```
public class Solution {
    public int solve(int[] A, int B) {
    int n = A.length;

    int result = 0;

    for (int i = 0; i < B; i++) {
      result += A[i];
    }

    int sum = result;

    for (int i = 0; i < B; i++) {
      sum -= A[B - 1 - i];
      sum += A[n - 1 - i];

      result = Math.max(result, sum);
    }

    return result;
    }
}
```
