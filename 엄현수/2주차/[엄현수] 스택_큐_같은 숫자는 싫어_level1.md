> https://school.programmers.co.kr/learn/courses/30/lessons/12906
>
> Stack 방법으로도 ArrayList 방법으로도 풀어봤는데, ArrayList가 효율성, 속도 면에서 압도적이었다.

```java
import java.util.*;

public class Solution {
    public int[] solution(int []arr) {
        
        Stack<Integer> stack = new Stack<>();
        stack.push(arr[0]);

        for(int i = 0; i < arr.length; i++) {
            if (stack.peek() != arr[i]) {
                stack.push(arr[i]);
            }
        }

        int answer [] = new int[stack.size()];
        for(int i = stack.size() - 1; i >= 0; i--) {
            answer[i] = stack.pop();
        }     
        
        return answer;                
        
        // int count = -1;
        // var v = new ArrayList<Integer>();
        // for(int i = 0; i<arr.length; i++) {
        // 	if(arr[i] != count) 
        // 		v.add(arr[i]);
        // 	count = arr[i];
        // }
        // int[] answer = new int[v.size()];
        // for(int i = 0; i<v.size(); i++) {
        // 	answer[i] = v.get(i);
        // }
        // return answer;
    }
}
```
