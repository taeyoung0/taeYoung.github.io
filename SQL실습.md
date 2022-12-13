1.SQL(Structured Query Language)

-관계형 데이터베이스에서 데이터의 정의(DDL),조작(DML),제어(DCL)를 위해 사용하는 언어
-표준 SQL:ISO의 표준 규격을 따르는 SQL

1.1 SQL기본 작성 규칙
      ->문장 마지막은 세미콜론(;)으로 끝남
      ->명령어,객체명,변수명은 대/소문자 구분이 없음 (데이터값은 대/소문자 구분함)
      ->날짜와 문자열에는 작은 따옴표를 사용
      ->단어와 단어 사이는 공백 또는 줄바꿈으로 구분

1.2 주석문

      -> -- 이것은 주석입니다.
      -> /* 여기부터
            여기까지 주석입니다 */

1.3 SELECT

-테이블에 존재하는 레코드의 값을 조회
-SELECT [ALL/DISTINCT] 칼럼1, 칼럼2, ``` FROM 테이블명
-ex) SELECT PLAYER_ID, PLAYER_NAME, TEAM_ID, POSITION
     FROM PLAYER;
-ALL: 중복 데이터 모두 출력(default)
-DISTINCT: 중복 데이터를 1건으로 출력 (SELECT DISTINCT)
 ->DISTINCT 키워드는 첫 칼럼의 앞에 위치해야 함
  ->칼럼의 조합에 대해 중복 체크
  ->NULL값도 하나의 값으로 간주함

1.4 SELECT * FROM 테이블명;
  ->해당 테이블의 모든 칼럼값 조회

1.5 SELECT -별칭 사용
-조회 결과에 일종의 별칭(ALIAS)을 부여하여 칼럼 레이블을 변경함
-칼럼명과 별칭 사이에 AS키워드를 사용 (optional)
-별칭이 공백,특수문자 등을 포함하는 경우 큰 따옴표 사용

1.6 ORDER VY
- 출력시 정렬 기준 설정
- SQL 문장의 맨 마지막에 위치
- 오름차순: ASC(생략 가능), 내림차순: DESC
   -> 참고) ORACLE에서 NULL은 가장 큰 값으로 취급됨
   ->ex) 선수명과 키를 키 오름차순으로 출력
           SELECT PLAYER_NAME, HEIGHT
      FROM PLAYER
      ORDER BY HEIGHT ASC;
    = 
           SELECT PLAYER_NAME, HEIGHT
      FROM PLAYER
      ORDER BY 2;
      ..
      