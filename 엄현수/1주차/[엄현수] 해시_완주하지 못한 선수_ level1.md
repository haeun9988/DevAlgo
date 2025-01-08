> https://school.programmers.co.kr/learn/courses/30/lessons/42576
>
> Arrays.sort() 정렬 함수를 사용하여 첫번째로 풀고
> <br>HashMap을 사용하여 key에 사람 이름을, value로 몇명인지를 각각 넣어서 출발자랑 완주자랑 사람 수가 다르면 반환하도록

```java
import java.util.*;

class Solution {
    public String solution(String[] participant, String[] completion) {
        HashMap<String, Integer> runner = new HashMap<>();
        HashMap<String, Integer> finisher = new HashMap<>();
        
        for(int i = 0; i < participant.length; i++) {
            runner.put(participant[i], runner.getOrDefault(participant[i], 0)+1);
            if(i < participant.length - 1)
                finisher.put(completion[i], finisher.getOrDefault(completion[i], 0)+1);                
        }
        
        for(int i = 0; i < participant.length; i++) {
            if(i == participant.length - 1) 
                return participant[i];
            
            if(finisher.get(participant[i]) == null)    // 완주자에 참가자가 없다면 반환
                return participant[i];
            
            if(finisher.get(participant[i]).equals(runner.get(participant[i]))) // 효율성을 위하여 equals함수 사용
                continue;
            else
                return participant[i];
            
        }
        
        
        
//         Arrays.sort(participant);
//         Arrays.sort(completion);

//         for(int i = 0; i < participant.length; i ++){
//             if(i == participant.length - 1)
//                 return participant[i];

//             if(!participant[i].equals(completion[i]))
//                 return participant[i];
//         }
        
        
        return "";
    }
}
```
