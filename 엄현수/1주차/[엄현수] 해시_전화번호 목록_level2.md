> https://school.programmers.co.kr/learn/courses/30/lessons/42577
>
> 사전순으로 정렬 후 뒤의 값이 앞의 값으로 시작하는 지 확인

```java
import java.util.*;

class Solution {
    public boolean solution(String[] phone_book) {
        boolean answer = true;
        
        Arrays.sort(phone_book);
        
        for(int i = 1; i < phone_book.length; i++) {
            if(phone_book[i].startsWith(phone_book[i-1]))
                return false;
        }
        
        return answer;
    }
}
```
