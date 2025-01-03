> https://school.programmers.co.kr/learn/courses/30/lessons/12909
>
> 역시나 스택보다 하드코딩이 빠르다. 

```java
import java.util.*;

class Solution {
    boolean solution(String s) {
        boolean answer = true;

        if(s.charAt(0) == ')')
            return false;

        Stack<Character> stack = new Stack<>();
        
        for(int i = 0; i < s.length(); i++) {
            stack.push(s.charAt(i));
        }

        int count = 0;
        while (!stack.isEmpty()) {
            if(stack.pop() == ')') {
                count++;
            }
            else count--;
            
            if(count == -1)
                return false;
        }

        return answer;
        

//         boolean answer = false;
//         int count = 0;
        
//         if(s.charAt(0) == ')' || s.charAt(s.length()-1) == '(')
//             return answer;

//         for(char c : s.toCharArray()) {
//             if(c == '(')
//                 count++;
//             else count--;
            
//             if(count == -1) break;
//         }
        
//         if(count == 0) answer = true;
//         return answer;
    }
}
```
