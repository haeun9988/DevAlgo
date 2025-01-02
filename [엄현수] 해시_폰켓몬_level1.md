> https://school.programmers.co.kr/learn/courses/30/lessons/1845?language=java

> HashSet을 쓰면 중복이 제거된다고 하여 사용
> <br>푼 후에 stream을 사용하여 푸는 방법도 검색

```java
import java.util.*;
import java.util.stream.Collectors;


class Solution {
    public int solution(int[] nums) {
//         HashSet<Integer> num = new HashSet<>();
        
//         for(int n : nums) {
//             num.add(n);
//         }
        
        HashSet<Integer> num = Arrays.stream(nums)
                             .boxed()
                             .collect(Collectors.toCollection(HashSet::new));

        
        int max = nums.length / 2;
                
        return Math.min(max, num.size());
    }
}
```
