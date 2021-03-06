# 7장 응용 계층: 애플리케이션에 데이터 전송하기

## 응용 계층의 역할

- 사용자가 하고 싶은 일을 할 수 있도록 하는 계층

- 서비스를 요청하는 측 / 서비스를 제공하는 측으로 구분

  - 요청 -> 클라이언트
  - 제공 -> 서버

- 사용자 측에서 사용하는 애플리케이션(클라이언트)

  - 웹 브라우저
  - 메일 프로그램

- 서비스를 제공 (서버)

  - 웹 서버 프로그램
  - 메일 서버 프로그램

### 프로토콜

- 클라이언트와 서버가 통신하기 위해선 응용 계층의 프로토콜 사용해야한다.

  | 프로토콜 |      내용      |
  | :------: | :------------: |
  |   HTTP   | 웹 사이트 접속 |
  |   DNS    |   이름 해석    |
  |   FTP    |   파일 전송    |
  |   SMTP   |   메일 송신    |
  |   POP3   |   메일 수신    |

## 웹 서버의 구조(웹 사이트 접속)

- WWW는 세가지 기술을 사용한다.
  - HTML
  - URL
  - HTTP

### HTML

- 하이퍼텍스트(hypertext)를 작성하는 마크업 언어

- 웹 페이지에서 문장 구조나 문자를 꾸미는 태그를 사용하는 마크업 언어

- 문장 구조를 지정하거나 이미지 파일을 보여 줄 떄도 태그를 사용

- 하이퍼링크를 사용할 수 있다.

### HTTP

- 클라이언트는 웹사이트를 보기 위해 서버(웹 서버)의 80번 포트를 사용하여 HTTP 통신한다.

- HTTP 요청을 보내고 서버에서 HTTP 응답을 반환한다.

  - 요청시 GET이라는 요청 정보, 파일 이름, 버전 등을 서버에 전송한다.
  - 응답으로 OK라는 정보와 index.html을 반환한다.

- keep-alive

  - 연결을 한 번 수립하면 데이터 교환을 마칠 때 까지 유지한다.
  - HTTP/1.1 버전에서 추가된 기능이다.
  - 요청 순서
    1. 연결 수립
    2. 요청
    3. 응답
    4. 연결 끊기

- HTTP/2

  - 이전 요청을 처리하는 데 시간이 길어지면 다음 요청에 대한 처리가 늦어지는 HTTP/1.1의 단점을 보완

  - 요청을 보낸 순서대로 응답 반환을 하지 않아도 된다.

## DNS 서버의 구조(이름 해석)

- URL을 IP 주소로 변환하는 서비스(시스템)이다.

### 도메인 이름

- 컴퓨터나 네트워크를 식별하기 위해 붙여진 이름

  - www.gilbut.co.kr과 같은 형식

- 호스트 이름(서버 이름)

  - 도메인 이름 앞에 있음.
  - `www`

- 이름 해석

  - 사용자의 접속 편의를 위해 http://www.gilbut.co.kr같은 주소를 DNS 서버가 IP 주소로 풀어주는 작업

- DNS 서버는 전 세계에 흩어져 있으므로 연계하면서 동작한다.

## 메일 서버의 구조 (SMTP와 POP3)

### 메일의 송수신 구조

- 클라이언트 측 메일 프로그램과 서버 측 메일 서버 프로그램 간에 통신이 필요하다.

- SMTP

  - 메일을 보내는 데 사용되는 프로토콜
  - 25번 포트

- POP3

  - 메일을 받는 데 사용하는 프로토콜
  - 110번 포트

- 동작 순서
  1. SMTP를 사용하여 컴퓨터 1에서 메일 서버 1로 메일을 보낸다.
  2. SMTP를 사용하여 메일 서버 1에서 메일 서버 2로 메일을 보낸다.
  3. POP3를 사용하여 메일 서버 2에서 컴퓨터 2로 메일 데이터를 보낸다.

### SMTP에 의한 메일 송신과 메일 전송

1. 세션 시작을 통지한다.

2. 송신자의 메일 주소를 통지한다.

3. 목적지 메일 주소를 통지한다.

4. 메일 본문 전송을 통지한다.

5. 메일 본문을 송신한다.

6. 세션 종료를 통지한다.

### POP3에 의한 메일 수신

- 메일 서버의 메일 박스에서 메일을 가져와 컴퓨터로 전송

- 메일 수신시 사용자 정보를 이용한 `사용자 인증`이 필요하다.

1. 세션을 시작한다.

2. 컴퓨터에서 받는 사람의 사용자 이름을 통지하고 메일 서버에 'OK'라는 확인 응답을 반환한다.

3. 수신자의 비밀번호를 통지하고 메일 서버 2에 비밀번호 확인이라는 확인 응답을 반환한다.

4. 메일을 확인하고 메일 서버는 '있음'이라는 확인 응답을 반환한다.

5. 메일 박스에 보관된 이메일을 전송받는다.

6. 세션을 종료한다.
