### Question:
https://leetcode.com/problems/letter-combinations-of-a-phone-number/

### Algo:
Backtracking

### Sol:
```
class Solution {
    public List<String> letterCombinations(String digits) {
        if (digits.length() == 0) return new ArrayList<>();
        
        String[] dict = new String[] {"", "", "abc", "def", "ghi", "jkl", "mno", "pqrs", "tuv", "wxyz" };
        List<String> combos = new ArrayList<>();
        backtrack(combos, digits.toCharArray(), "", dict);
        return combos;
    }
    
    public void backtrack(List<String> combos, char[] digits, String s, String[] dict) {
        if (s.length() == digits.length) { combos.add(s); return; }
        int i = s.length();
        int digit = digits[i] - '0';
        for (char letter : dict[digit].toCharArray()) {
            backtrack(combos, digits, s + Character.toString(letter), dict);
        }
    }
}
```

### Sol2:
```
class Solution {
    Map<Character, List<Character>> phoneNumber = new HashMap<>();
    public List<String> letterCombinations(String digits) {
        List<String> res = new ArrayList<>();
        if(digits.isEmpty())
            return res;
        
        phoneNumber.put('2', Arrays.asList('a', 'b', 'c'));
        phoneNumber.put('3', Arrays.asList('d', 'e', 'f'));
        phoneNumber.put('4', Arrays.asList('g', 'h', 'i'));
        phoneNumber.put('5', Arrays.asList('j', 'k', 'l'));
        phoneNumber.put('6', Arrays.asList('m', 'n', 'o'));
        phoneNumber.put('7', Arrays.asList('p', 'q', 'r', 's'));
        phoneNumber.put('8', Arrays.asList('t', 'u', 'v'));
        phoneNumber.put('9', Arrays.asList('w', 'x', 'y', 'z'));
        
        generateCombination(digits, 0, "", res);
        return res;
    }
    
    public void generateCombination(String digits, int index, String pattern, List<String> res) {
        if(index == digits.length()) {
            res.add(pattern);
            return;
        }
        
        List<Character> list = phoneNumber.get(digits.charAt(index));
        
        for(Character c: list) {
            generateCombination(digits, index + 1, pattern + String.valueOf(c), res);
        }   
    }
}
```
