### Question:
https://leetcode.com/problems/decode-string/

### Algo:
String

### Sol:
```
class Solution {
    public String decodeString(String s) {
        
        Stack<Integer> countStack = new Stack<>();
        Stack<String> wordStack = new Stack<>();
        int number = 0;
        StringBuilder word = new StringBuilder();
        
        for(int i = 0; i < s.length(); i++) {
            char ch = s.charAt(i);
            if(Character.isDigit(ch)) {
               number = number * 10 + (ch - '0');
            }else if(Character.isLetter(ch)) {
               word.append(ch);
            }else if(ch == '[') {
                //adding the count
                countStack.push(number);
                //adding the current word to stack
                wordStack.push(word.toString());
                //reset word for nested string
                word = new StringBuilder(); 
                //reset number for nested count
                number = 0;
            } else {
                StringBuilder duplicateWord = new StringBuilder(wordStack.pop());
                int count = countStack.pop();
                for(int j = 1; j <= count; j++) {
                    duplicateWord.append(word);
                }
                
                word = duplicateWord;
            }
        }
        
        return word.toString();
    }
}
```
