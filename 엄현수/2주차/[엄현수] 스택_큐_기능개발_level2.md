> https://school.programmers.co.kr/learn/courses/30/lessons/42586
>
> 큐를 사용하여 남은 시간을 큐에 저장하고 하나를 뽑고, 뒤랑 비교하면서 해결

```java
import java.util.*;

class Solution {
    public int[] solution(int[] progresses, int[] speeds) {
        List<Integer> answer = new ArrayList<>();
        Queue<Integer> q = new LinkedList<>();

        int num = 0;
        for (int i = 0; i < progresses.length; i++) {
            num = (100 - progresses[i]) / speeds[i];
            if ((100 - progresses[i]) % speeds[i] != 0) {
                num++;
            }
            q.offer(num);
        }

        while (!q.isEmpty()) {
            int count = 1;
            int current = q.poll();
            int next;

            while(!q.isEmpty()) {
                next = q.peek();
                if (current >= next) {
                    count++;
                    q.poll();
                }
                else break;
            }
            
            answer.add(count);
        }
        
        return answer.stream().mapToInt(Integer::intValue).toArray();
    }
}
```
