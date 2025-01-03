> https://school.programmers.co.kr/learn/courses/30/lessons/42578
>
> HashMap을 사용하여 의상 종류별로 개수를 세고 경우의 수를 세었음.

```java
import java.util.*;

class Solution {
    public int solution(String[][] clothes) {
        int answer = 1;
        
        HashMap<String, Integer> cloth = new HashMap<>();
        
        for(String s[] : clothes) {
            cloth.put(s[1], cloth.getOrDefault(s[1], 0) + 1);   // 의상 종류별 개수
        }
        
        for(String key : cloth.keySet()) {
            answer *= cloth.get(key) + 1;   // 종류별 의상 개수 + 1 을 서로 곱
        }
        
        return answer - 1;  // 아무것도 안입는 경우 빼기
    }
}
```
