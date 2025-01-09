# 문제 링크
https://school.programmers.co.kr/learn/courses/30/lessons/59405

# 풀이 방법
1. `ANIMAL_INS` 테이블에서 `NAME` 조회
2. `DATETIME` 기준 오름차순 정렬
3. `LIMIT 1`로 상위 데이터 1개만 반환

```sql 
SELECT NAME
FROM ANIMAL_INS
ORDER BY DATETIME ASC
LIMIT 1;
```