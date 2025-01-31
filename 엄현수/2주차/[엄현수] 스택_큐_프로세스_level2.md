> https://school.programmers.co.kr/learn/courses/30/lessons/42587
>
> 우선순위를 넣을 큐와 인덱스를 알려줄 큐 총 2개를 써서 해결.

```java
import java.util.LinkedList;
import java.util.Queue;

class Solution {
    public int solution(int[] priorities, int location) {
        int answer = 0;
        int count = 0;
        Queue<Integer> q = new LinkedList<>();
        Queue<Integer> q2 = new LinkedList<>();

        for (int i = 0; i < priorities.length; i++) {
            q.add(priorities[i]);
            q2.add(i);
        }

        while (!q.isEmpty()) {
            int flag = 0;
            int num = q.peek();
            for (int i : q) {
                if (i > num) {
                    flag++;
                    break;
                }
            }
            if (flag == 0) {
                q.poll();
                count = q2.poll();
                answer++;
                if (count == location)
                    break;
            } else {
                q.add(q.poll());
                q2.add(q2.poll());
            }
        }

        return answer;
    }
}
```
