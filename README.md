# :pencil2: **CS-study Repository**

> ### Computer Science Study for Technical Interview
>
> ### 2021년 9월 1일 개설된 Techeer의 Computer Science 스터디 레포입니다. <br>
>
> ### 야! 너두 CS할 수 있어!

<br>

## :mag_right: Content

- [스터디 운영 규칙](#-스터디-운영-규칙)
  - [스터디 운영 방식](#스터디-운영-방식)
  - [스터디 규칙](#스터디-규칙)
- [네트워크](#네트워크)
  - [네트워크 목차](#네트워크-목차)
  - [네트워크 참여 현황](#네트워크-참여-현황)
- [OS](#os)
  - [OS 목차](#os-목차)
  - [OS 참여 현황](#os-참여-현황)
- [DB](#db)
  - [DB 목차](#db-목차)
  - [DB 참여 현황](#db-참여-현황)

<br>

## :loudspeaker: 스터디 운영 규칙

### 스터디 운영 방식

1. 네트워크, OS, DB 각각에서 주차별 주제를 학습하고 정리합니다.
2. [Issues](https://github.com/EunjiShin/CS-study/issues) 에서 주차별 issue의 코멘트에 학습내용을 정리한 결과물을 첨부합니다. `개인 Github Repo, 기술 블로그, 사진..` 무엇이든 상관없습니다.
3. 2주에 한 번씩 학습한 내용들을 기반으로 4-5분 동안의 온라인 발표를 진행합니다. 발표자는 당일 랜덤으로 8명을 추첨하여 뽑습니다. 누가 뽑힐지 모르니 모두 발표 준비를 해야겠죠?
4. 발표 자료는 필수이며, 양식은 자유입니다. (Ex. PPT, PDF, 한글, 등..)

<br>

### 스터디 규칙

1. 참여 체크는 매주 월요일에 진행할 예정입니다. (월-일까지 1주 돌고, 다음 월요일에 전주 학습 참여를 체크)
2. 1회 불참 벌금, 2회 불참 발표 필수 + 벌금, 3회 불참 퇴출입니다.
3. 만약 불참 사유가 있다면 최소 토요일까지 운영자(신은지)에게 Slack으로 연락 부탁드립니다. (시험기간 포함)

<br>

## 네트워크

### 네트워크 목차

> `모두의 네트워크`, `그림으로 배우는 HTTP & Network` 를 참고하며, 동시에 두 권을 공부합니다. <br>
> 아래 키워드를 중점적으로 공부합시다.
>
> - 웹과 네트워크 기본
> - 웹서버와 WAS
> - HTTP 헤더
> - 쿠키 헤더
> - HTTPS
> - 인증
> - RESTful

|                           주차                           |   모두의 네트워크   |     모네 주제      | 그림으로 배우는 HTTP & Network |                 그림HN 주제                 |
| :------------------------------------------------------: | :-----------------: | :----------------: | :----------------------------: | :-----------------------------------------: |
| [1주차](https://github.com/EunjiShin/CS-study/issues/3)  | 1장 (lesson 01~05)  | 네트워크 기본 지식 |          1장 (13-36p)          |            웹과 네트워크의 기본             |
| [2주차](https://github.com/EunjiShin/CS-study/issues/5)  | 2장 (lesson 06~08)  | 네트워크 통신 규칙 |          2장 (37-60p)          |                프로토콜 HTTP                |
| [3주차](https://github.com/EunjiShin/CS-study/issues/7)  | 3장 (lesson 09~11)  |     물리 계층      |          3장 (62-76p)          |                 HTTP 메시지                 |
| [4주차](https://github.com/EunjiShin/CS-study/issues/11) | 4장 (lesson 12~16)  |  데이터 링크 계층  |          4장 (77-90p)          |               HTTP 상태 코드                |
| [5주차](https://github.com/EunjiShin/CS-study/issues/13) | 5장 (lesson 17~22)  |   네트워크 계층    |       5-6.2장 (91-112p)        |           웹 서버, HTTP 헤더 (1)            |
| [6주차](https://github.com/EunjiShin/CS-study/issues/16) | 6장 (lesson 23~27)  |     전송 계층      |      6.3-6.4장 (113-154p)      | HTTP/1.1 일반 헤더 필드, 리퀘스트 헤더 필드 |
| [7주차](https://github.com/EunjiShin/CS-study/issues/19) | 7장 (lesson 28~31)  |     응용 계층      |      6.5-6.6장 (155-171p)      |    리스폰스 헤더 필드, 엔티티 헤더 필드     |
|                          8주차                           | 8장 (lesson 32~034) | 네트워크 전체 흐름 |      6.7-6.8장 (172-182p)      |       쿠키 헤더 필드, 기타 헤더 필드        |
|                          9주차                           | 9장 (lesson 35~36)  |    무선 랜 통신    |         7장 (183-212p)         |          웹을 안전하게 하는 HTTPS           |
|                          10주차                          |       (종료)        |       (종료)       |         8장 (213-228p)         |                 액세스 인증                 |
|                          11주차                          |       (종료)        |       (종료)       |         9장 (229-248p)         |        HTTP에 기능을 추가한 프로토콜        |
|                          12주차                          |       (종료)        |       (종료)       |        10장 (249-262p)         |         웹 콘텐츠에서 사용하는 기술         |
|                          13주차                          |       (종료)        |       (종료)       |     11.1-11.2장 (263-292p)     |          웹 공격 기술, 취약성 (1)           |
|                          14주차                          |       (종료)        |       (종료)       |     11.3-11.5장 (293-314p)     |              취약성(2,3), 기타              |

<br>

### 네트워크 참여 현황

| 참여자   | 1주차              | 2주차              | 3주차              | 4주차              | 5주차              | 6주차              | 7주차 | 8주차 | 9주차 | 10주차 | 11주차 | 12주차 | 13주차 | 14주차 |
| -------- | ------------------ | ------------------ | ------------------ | ------------------ | ------------------ | ------------------ | ----- | ----- | ----- | ------ | ------ | ------ | ------ | ------ |
| 김민웅   | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: |       |       |       |        |        |        |        |        |
| 김서경   | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: |       |       |       |        |        |        |        |        |
| 김서연   | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: |       |       |       |        |        |        |        |        |
| 김서영   | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: |       |       |       |        |        |        |        |        |
| 김소미   | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: |       |       |       |        |        |        |        |        |
| 맹수연   | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: |       |       |       |        |        |        |        |        |
| 박근우   | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: |       |       |       |        |        |        |        |        |
| 서연주   | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: |       |       |       |        |        |        |        |        |
| 신은지   | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: |       |       |       |        |        |        |        |        |
| 오현택   | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: |       |       |       |        |        |        |        |        |
| 용길한   | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: |                    |       |       |       |        |        |        |        |        |
| 장동현   | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: |       |       |       |        |        |        |        |        |
| Ryan Lee | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: |       |       |       |        |        |        |        |        |

<br>

## OS

### OS 목차

> `Operating System Concepts`책과 [여기](http://www.kocw.or.kr/home/cview.do?cid=4b9cd4c7178db077)의 강의를 참고합니다. <br>
> 주차별 진도는 2시간 내외로 잘랐습니다. 2학점짜리 교양 하나 더 듣는다고 생각합시다! <br>
> 아래 키워드를 중점적으로 공부합시다.
>
> - 세마포어, 데드락
> - 스레드, 멀티 스레드
> - 인터럽트

|                           주차                           |         주제         |                                                                                                                                                                             강의                                                                                                                                                                             |
| :------------------------------------------------------: | :------------------: | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
| [1주차](https://github.com/EunjiShin/CS-study/issues/1)  |    운영체제 개요     |                                                                                                          [1-1](https://core.ewha.ac.kr/publicview/C0101020170306154617836038), [1-2](https://core.ewha.ac.kr/publicview/C0101020170308134855263835)                                                                                                          |
| [2주차](https://github.com/EunjiShin/CS-study/issues/6)  | 컴퓨터 시스템의 구조 |                                    [2-1](https://core.ewha.ac.kr/publicview/C0101020170313141353779888), [2-2](https://core.ewha.ac.kr/publicview/C0101020170313145811055991), [2-3](https://core.ewha.ac.kr/publicview/C0101020170313151303541331), [2-4](https://core.ewha.ac.kr/publicview/C0101020170315134644924991)                                    |
| [3주차](https://github.com/EunjiShin/CS-study/issues/8)  |    프로세스 관리     | [3-1](https://core.ewha.ac.kr/publicview/C0101020170320142246460343), [3-2](https://core.ewha.ac.kr/publicview/C0101020170320150008154282), [3-3](https://core.ewha.ac.kr/publicview/C0101020170320151704028225), [3-4](https://core.ewha.ac.kr/publicview/C0101020170322131206999075), [3-5](https://core.ewha.ac.kr/publicview/C0101020170322134548803842) |
| [4주차](https://github.com/EunjiShin/CS-study/issues/12) |     CPU 스케줄링     |                                    [4-1](https://core.ewha.ac.kr/publicview/C0101020170327144547225686), [4-2](https://core.ewha.ac.kr/publicview/C0101020170327151556728127), [4-3](https://core.ewha.ac.kr/publicview/C0101020170329132536583694), [4-4](https://core.ewha.ac.kr/publicview/C0101020170329134735568510)                                    |
| [5주차](https://github.com/EunjiShin/CS-study/issues/15) |      병행 제어       |                                                                       [5-1](https://core.ewha.ac.kr/publicview/C0101020170403144233051510), [5-2](https://core.ewha.ac.kr/publicview/C0101020170403151644920369), [5-3](https://core.ewha.ac.kr/publicview/C0101020170405134621661588)                                                                       |
| [6주차](https://github.com/EunjiShin/CS-study/issues/17) |     병행 제어(2)     |                                                                       [6-1](https://core.ewha.ac.kr/publicview/C0101020170410151704945993), [6-2](https://core.ewha.ac.kr/publicview/C0101020170412130458495242), [6-3](https://core.ewha.ac.kr/publicview/C0101020170412134857472082)                                                                       |
| [7주차](https://github.com/EunjiShin/CS-study/issues/20) |        데드락        |                                                                                                                                              [7](https://core.ewha.ac.kr/publicview/C0101020170417145143139609)                                                                                                                                              |
|                          8주차                           |  메모리 관리 (1,2)   |                                                                                                          [8-1](https://core.ewha.ac.kr/publicview/C0101020170426134700534350), [8-2](https://core.ewha.ac.kr/publicview/C0101020170501151238245167)                                                                                                          |
|                          9주차                           |   메모리 관리 (3)    |                                                                                                                                             [9-1](https://core.ewha.ac.kr/publicview/C0101020170508150536565534)                                                                                                                                             |
|                          10주차                          |     가상 메모리      |                                                                                                         [10-1](https://core.ewha.ac.kr/publicview/C0101020140509151648408460), [10-2](https://core.ewha.ac.kr/publicview/C0101020170515151006966449)                                                                                                         |
|                          11주차                          |  파일 시스템 (1,2)   |                                                                                                         [11-1](https://core.ewha.ac.kr/publicview/C0101020140516150939191200), [11-2](https://core.ewha.ac.kr/publicview/C0101020140520134614002164)                                                                                                         |
|                          12주차                          |   파일 시스템 (3)    |                                                                                                                                            [12-1](https://core.ewha.ac.kr/publicview/C0101020170531135029378055)                                                                                                                                             |
|                          13주차                          |    입출력 시스템     |                                                                                                         [13-1](https://core.ewha.ac.kr/publicview/C0101020170605145841940007), [13-2](https://core.ewha.ac.kr/publicview/C0101020170607132025509144)                                                                                                         |

<br>

### OS 참여 현황

| 참여자   | 1주차              | 2주차              | 3주차              | 4주차              | 5주차              | 6주차              | 7주차 | 8주차 | 9주차 | 10주차 | 11주차 | 12주차 | 13주차 |
| -------- | ------------------ | ------------------ | ------------------ | ------------------ | ------------------ | ------------------ | ----- | ----- | ----- | ------ | ------ | ------ | ------ |
| 김민웅   | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: |       |       |       |        |        |        |
| 김서경   | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: |       |       |       |        |        |        |
| 김서영   | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: |       |       |       |        |        |        |
| 박근우   | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: |       |       |       |        |        |        |
| 서연주   | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: |       |       |       |        |        |        |
| 신은지   | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: |       |       |       |        |        |        |
| 오현택   | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: |       |       |       |        |        |        |
| 용길한   | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: |                    |       |       |       |        |        |        |
| Ryan Lee | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: |       |       |       |        |        |        |

<br>

## DB

### DB 목차

> `데이터베이스 첫 걸음`, `SQL 첫 걸음` 을 참고하며, 동시에 두 권을 공부합니다. <br>
> 연습문제는 분량에서 제외했습니다. 하지만 복습을 위해서 풀어보시는 것을 권장합니다. <br>
> 아래 키워드를 중점적으로 공부합시다.
>
> - RDB, NoSQL
> - ORM
> - 인덱싱
> - 트랜잭션
> - 정규화
> - 쿼리 최적화 등 성능 관련
> - 설계 ~ 구현

|                           주차                           | 데이터베이스 첫 걸음 |         데베첫 주제         |         SQL 첫 걸음          |                    SQL 주제                    |
| :------------------------------------------------------: | :------------------: | :-------------------------: | :--------------------------: | :--------------------------------------------: |
| [1주차](https://github.com/EunjiShin/CS-study/issues/2)  |     1장 (15-31p)     |       데이터베이스란?       |        1-2강 (22-39p)        |                  데이터베이스                  |
| [2주차](https://github.com/EunjiShin/CS-study/issues/4)  |     2장 (35-53p)     |     관계형 데이터베이스     |    3-4강 (40-47p, 52-60p)    |      데이터베이스 서버, Hello World 실행       |
| [3주차](https://github.com/EunjiShin/CS-study/issues/9)  |    3장 (57p-68p)     |  데이터베이스의 초기 비용   |        5-6강 (61-74p)        |        테이블 구조 참조, 검색 조건 지정        |
| [4주차](https://github.com/EunjiShin/CS-study/issues/10) |     3장 (69-80p)     |  데이터베이스의 운영 비용   |        7-8강 (75-89p)        |           조건 조합, 패턴 매칭 검색            |
| [5주차](https://github.com/EunjiShin/CS-study/issues/14) |    4장 (85-102p)     | 데이터베이스와 아키텍처 (1) |       9-10강 (94-107p)       |           정렬, 복수의 열 지정 정렬            |
| [6주차](https://github.com/EunjiShin/CS-study/issues/18) |   4장 (103p-115p)    | 데이터베이스와 아키텍처 (2) |      11-12강 (108-129p)      |                LIMIT, 수치 연산                |
| [7주차](https://github.com/EunjiShin/CS-study/issues/21) |    5장 (119-139p)    |       DBMS 기본 지식        |      13-15강 (130-147p)      |              문자열, 날짜, CASE문              |
|                          8주차                           |    6장 (143-164p)    |  SQL문의 기본 : SELECT (1)  |      16-19강 (152-177p)      |           데이터의 추가, 삭제, 갱신            |
|                          9주차                           |    6장 (165-190p)    |  SQL문의 기본 : SELECT (2)  |      20-22강 (182-203p)      |                  집계, 그룹화                  |
|                          10주차                          |    7장 (195-220p)    |   트랜잭션과 동시성 제어    |      23-24강 (204-223p)      |            서브쿼리, 상관 서브쿼리             |
|                          11주차                          |    8장 (225-239p)    |       테이블 설계 (1)       |      25-27강 (227-248p)      | DB 객체, 테이블 작성/삭제/변경, <br> 작성 제약 |
|                          12주차                          |    8장 (240-255p)    |       테이블 설계 (2)       |      28-30강 (249-269p)      |                   인덱스, 뷰                   |
|                          13주차                          |    9장 (261-273p)    |         백업과 복구         |      31-32강 (274-300p)      |               집합, 테이블 결합                |
|                          14주차                          |   10장 (279-289p)    |        성능 향상 (1)        | 33-34강 (304-308p, 312-318p) |              관계형 모델, DB 설계              |
|                          15주차                          |   10장 (290-309p)    |        성능 향상 (2)        |      35-36강 (319-333p)      |                정규화, 트랜잭션                |

<br>

### DB 참여 현황

| 참여자   | 1주차              | 2주차              | 3주차              | 4주차              | 5주차              | 6주차              | 7주차 | 8주차 | 9주차 | 10주차 | 11주차 | 12주차 | 13주차 |
| -------- | ------------------ | ------------------ | ------------------ | ------------------ | ------------------ | ------------------ | ----- | ----- | ----- | ------ | ------ | ------ | ------ |
| 김민웅   | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: |       |       |       |        |        |        |
| 김서경   | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: |       |       |       |        |        |        |
| 김서영   | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: |       |       |       |        |        |        |
| 김소미   | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: |       |       |       |        |        |        |
| 박근우   | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: |       |       |       |        |        |        |
| 서연주   | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: |       |       |       |        |        |        |
| 신은지   | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: |       |       |       |        |        |        |
| 오현택   | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: |       |       |       |        |        |        |
| 용길한   | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: |                    |       |       |       |        |        |        |
| Ryan Lee | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: |       |       |       |        |        |        |
