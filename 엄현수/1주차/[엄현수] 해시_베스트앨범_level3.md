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
            total.put(genres[i], total.getOrDefault(genres[i], 0) + plays[i]);
        }
        
        List<String> list = new ArrayList<>(total.keySet());
        list.sort((key1, key2) -> total.get(key2).compareTo(total.get(key1)));  // 장르 내림차순 정렬        
        
        for(String s : list) {  // 가장 많이 재생된 장르부터
            Map<Integer, Integer> playsList = new LinkedHashMap<>();
            for(int i = 0; i < plays.length; i++) {
                if(s.equals(genres[i]))
                    playsList.put(i, plays[i]);
            }
            
            List<Integer> songList = new ArrayList<>(playsList.keySet());
            songList.sort((key1, key2) -> playsList.get(key2).compareTo(playsList.get(key1)));

            for (int i = 0; i < Math.min(2, songList.size()); i++) {   // 상위 2곡까지만 선택
                answer.add(songList.get(i));
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
