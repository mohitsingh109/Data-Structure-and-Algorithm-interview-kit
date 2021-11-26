### Question
https://leetcode.com/problems/substrings-of-size-three-with-distinct-characters/

### Algo:
HashMap, Sliding Window

### Sol-1
```
class Solution {
    public int countGoodSubstrings(String s) {
        Map<Character, Integer> map = new HashMap<>();
        int windowStart = 0;
        int goodSubStrCount = 0;
        
        for(int windowEnd = 0; windowEnd < s.length(); windowEnd++) {
            char ch = s.charAt(windowEnd);
            map.put(ch, map.getOrDefault(ch, 0) + 1);
            if((windowEnd - windowStart + 1) == 3) {
                if(map.size() == 3)
                    goodSubStrCount++;
                
                char sch = s.charAt(windowStart++);
                map.put(sch, map.get(sch) - 1);
                if(map.get(sch) == 0)
                    map.remove(sch);
            }
        }
        
        return goodSubStrCount;
    }
}
```

### Sol-2:
```
public int countGoodSubstrings(String s) {
    int cnt[] = new int[123], repeat = 0, res = 0;
    for(int i = 0; i < s.length(); ++i) {
        if(cnt[s.charAt(i)] == 1) repeat++;
        cnt[s.charAt(i)]++;
        if( i >= 3 ){
            if(cnt[s.charAt(i-3)] == 2) repeat--;
            cnt[s.charAt(i-3)]--;
        }
        if(i >= 2 && repeat == 0) res++;
    }    
    return res;
}
```
