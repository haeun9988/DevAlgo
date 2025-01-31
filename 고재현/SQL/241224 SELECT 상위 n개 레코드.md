# SQL 고득점 Kit > SELECT > 상위 n개 레코드

## 문제 설명
- **요구사항**:  
`ANIMAL_INS` 테이블에서 다음 조건을 만족하는 데이터를 조회하는 SQL 쿼리를 작성합니다:
  1. 동물 보호소에 가장 먼저 들어온 동물의 이름(NAME)을 조회.
  2. 보호 시작일(DATETIME)을 기준으로 가장 오래된 기록을 가져옵니다.

## 문제 링크
https://school.programmers.co.kr/learn/courses/30/lessons/59405

## 간단한 풀이 방법
1. `ORDER BY`를 사용하여 보호 시작일(DATETIME)을 오름차순(ASC)으로 정렬.
2. `LIMIT`을 사용하여 상위 1개의 데이터만 선택.

## 코드 설명
### 작성한 SQL 코드:
```sql
SELECT NAME
FROM ANIMAL_INS
ORDER BY DATETIME ASC
LIMIT 1;
```