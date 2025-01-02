> https://school.programmers.co.kr/learn/courses/30/lessons/42579
>
> HashMap에 먼저 장르별 총 재생횟수를 넣고 가장 많이 재생한 장르부터 두 곡을 뽑았다.


```java
import java.util.*;

class Solution {
    public int[] solution(String[] genres, int[] plays) {
        // 장르별로 재생횟수를 모두 더한 다음 최고로 많이 재생된 장르를 찾는다.
        // 그 장르에 해당하는 번호만 뽑아서 정렬을 시킨다.
        // 장르 순서대로 두개씩만 뽑아서 배열에 집어넣는다.
        
        List<Integer> answer = new ArrayList<>();
        
        HashMap<String, Integer> total = new HashMap<>();
        
        for(int i = 0; i < genres.length; i++) {    // 장르별 재생횟수 더하기
            if(total.get(genres[i]) == null) {
                total.put(genres[i], plays[i]);
            }
            else {
                total.put(genres[i], total.get(genres[i]) + plays[i]);                
            }
        }
        
        List<Map.Entry<String, Integer>> list = new ArrayList<>(total.entrySet());        
        list.sort((entry1, entry2) -> entry2.getValue().compareTo(entry1.getValue())); // 장르 내림차순 정렬
        
        
        for(Map.Entry<String, Integer> entry : list) {  // 가장 많이 재생된 장르부터
            Map<Integer, Integer> playsList = new LinkedHashMap<>();
            for(int i = 0; i < plays.length; i++) {
                if(entry.getKey().equals(genres[i]))
                    playsList.put(i, plays[i]);
            }
            
            List<Map.Entry<Integer, Integer>> entryList = new ArrayList<>(playsList.entrySet());
            entryList.sort((entry1, entry2) -> entry2.getValue().compareTo(entry1.getValue()));

            for (int i = 0; i < Math.min(2, entryList.size()); i++) {   // 상위 2곡까지만 선택
                answer.add(entryList.get(i).getKey());
            }
            
        }
        int arr[] = new int[answer.size()];
        for(int i = 0; i < answer.size(); i++) {
            arr[i] = answer.get(i);
        }
        
        return arr;
    }
}
```
