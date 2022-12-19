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
      
1.7 WHERE 절
  -특정조건을 만족하는 데이터를 한정하기 위해 사용
  -SELECT ~ FROM ~ WHERE ~ 형태로 사용
  EX) SELECT PLAYER_ID, POSITION
      FROM PLAYER
      WHERE POSITION = 'GK'

  -산술 연산자: +, -, *, /
  -비교 연산자: =, <>, <, >, <=, >=
  -논리 연산자:  AND, OR, NOT
  -SQL 연산자: ||, BETWEEN a AND b, IN(LIST), LIKE'비교 문자열, IS NULL

   * 산술 연산자
   -NUMBER와 DATE 자료형에 대해 적용
   EX) SELECT PLAYER_NAME
       FROM PLAYER
       WHERE ( (HEIGHT-100) * 0.9 - WEIGHT) > 0 ;
  
   * 비교 연산자
   -모든 자료형에 대해 적용
   -문자열의 크기 비교는 사전 순으로 수행 됨
   -EX) '01' < '02' < '1' < '11' < '2'
   -NULL에는 비교 연산자는 사용 불가

   * 논리 연산자
    -EX) SELECT PLAYER_NAME, POSITION, HEIGHT FROM PLAYER
         WHERE NOT(POSITION = 'GK' AND HEIGHT > 180);
         = NOT 연산자가 괄호안의 AND를 만나게 되면 AND는 OR로 바뀌게 된다
         -> SELECT PLAYER_NAME, POSITION, HEIGHT FROM PLAYER
            WHERE NOT(POSITION = 'GK') OR NOT(HEIGHT > 180);
  
   * SQL 연산자
   -합성(연결) 연산자 문자열과 문자열을 연결함
   -방법1: CONCAT(str1, str2)
   -방법2: str1 || str2
   -EX) SELECT PLAYER_NAME, HEIGHT || 'CM' AS "선수 신장"
        FROM PLAYER;
   
   -BETWEEN
   ->EX) SELECT PLAYER_NAME 선수이름, POSTION 포지션, HEIGHT 키
         FROM PLAYER
         WHERE HEGIHT BETWEEN 170 AND 180;
   
   -NOT BETWEEN
   ->EX) SELECT PLAYER_NAME 선수이름, POSTION 포지션, HEIGHT 키
         FROM PLAYER
         WHERE HEGIHT NOT BETWEEN 170 NOT 180; 
   
   -IN(LIST)
   ->EX) SELECT PLAYER_NAME 선수이름, TEAM_ID, POSTION
         FROM PLAYER
         WHERE (TEAM_ID, POSITION) IN ( ('K04', 'GK'), ('K06', 'MF')) ;
   
   -NOT IN
   ->EX) SELECT PLAYER_NAME 선수이름, TEAM_ID, POSTION
         FROM PLAYER
         WHERE (TEAM_ID, POSITION) NOT IN ( ('K04', 'GK'), ('K06', 'MF')) ;
   
  - LIKE
  ->문자열 비교 연산
  ->와일드 카드 사용가능 ('%' 임의의 문자 N개 / '_' 임의의 문자 1개)

  -ROWNUM (TOP N개의 레코드 반환)
  -> ROWNUM 사용자가 아닌 시스템이 관리하는 Pseudo Column
  -> 채번, 출력 개수 지정 등에 활용 가능
  ->EX) SELECT PLAYER_NAME, ROWNUM
        FROM PLAYER;
  ->테이블 내의 UNIQUE한 값 설정에도 사용 가능
  ->ROWNUM을 이용하여 ID필드 생성
  ->UPDATE 테이블명 SET 칼럼명 = ROWNUM;
  


   
