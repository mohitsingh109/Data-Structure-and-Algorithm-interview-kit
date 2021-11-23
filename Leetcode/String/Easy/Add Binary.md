### Question:
https://leetcode.com/problems/add-binary/

### Algo:
binary number

### Sol:
```
class Solution {
    public String addBinary(String a, String b) {
        StringBuilder sb = new StringBuilder();
        int i = a.length() - 1;
        int j = b.length() - 1;
        int carry = 0;
        
        while(i >=0 || j>=0){
            int sum = carry;
            sum += i >= 0? a.charAt(i) - '0': 0;
            sum += j >= 0? b.charAt(j) - '0': 0;
            sb.append(sum%2);
            carry = sum/2;
            i--; j--;
        }
        if(carry == 1) sb.append(carry);
        return sb.reverse().toString();
    }
}

/*
Binary Addition

0 + 0 = 0
1 + 0 = 1
0 + 1 = 1
1 + 1 = 10 ---> (here {1} is carry)
*/
```
