> https://school.programmers.co.kr/learn/courses/30/lessons/42583
>
> 트럭의 무게와 다리에 올라간 시점을 저장하는 클래스 Truck을 만들고 큐로 해결

```java
import java.util.*;

class Solution {
       public static class Truck {
            int weight, position;

            public Truck(int weight, int position) {
                this.weight = weight;
                this.position = position;
            }
        }
    
    public int solution(int bridge_length, int weight, int[] truck_weights) {
        Deque<Truck> bridge = new ArrayDeque<>();

        int time = 0;   // 경과 시간
        int bridgeWeight = 0;   // 다리 위에 있는 트럭의 무게 합
        int idx = 0;    // 대기 트럭 인덱스
        while(!bridge.isEmpty() || idx < truck_weights.length) {
            time++;

            if(!bridge.isEmpty()) { // 다리 위에 트럭이 있는 경우
                Truck frontTruck = bridge.peek();  // 맨앞에 있는 트럭 확인
                if(time - frontTruck.position >= bridge_length) {  // 그 트럭이 다리를 다 지나갔는지 확인
                    bridgeWeight -= frontTruck.weight;
                    bridge.poll();
                }
            }

            if(idx < truck_weights.length) {    // 대기 트럭이 있다면
                // 다리 위 트럭 무게와 다음 트럭 무게를 합친 것이 가능 무게보다 작고 다리 위에 올라가 있는 트럭 수가 최대 수보다 작다면 삽입
                if(bridgeWeight + truck_weights[idx] <= weight && bridge.size() < bridge_length) {
                    bridge.offer(new Truck(truck_weights[idx], time));  // 다리에 얹기
                    bridgeWeight += truck_weights[idx]; // 다리 무게 추가
                    idx++;  // 다음 대기 트럭
                }
            }

        }

        return time;
    }
}
```
