# 간단한 프로토콜 HTTP

## HTTP를 통한 클라이언트와 서버 간 통신

- 2대의 컴퓨터 간 통신의 경우 한 번 통신을 할 때 반드시 어느 한 쪽은 클라이언트,  
  다른 한쪽은 서버가 된다.

<br>

## 리퀘스트와 리스폰스를 교환하여 성립

### Request 내용

> GET /index.html HTTP /1.1  
> Host: www.hackr.jp  
> Connection: keep-alive  
> Content-Type: application/x-www-form-urlencoded  
> Content-Length: 16
>
> name=ueno&age=37

- 메소드 - GET

  - 서버에 요구하는 종류를 나타낸다.
  - GET / POST / DELETE / PUT 등이 있다.

- URI - /index.html

  - 요구 대상인 리소스를 나타낸다.

- 프로토콜 버전 - HTTP /1.1

  - 클라이언트 기능을 식별하기 위한 HTTP 버전 번호

- 헤더 필드 - Host ~ Content-Length

- 엔티디 - name

### Response 내용

> HTTP /1.1 200 OK  
> Date: Tue, 10 Jul 2012 06:50:15 GMT  
> Content-Length: 362  
> Content-Type: text/html
>
> \<html>  
> ...

- 프로토콜 버전 - HTTP /1.1

  - 서버의 HTTP 버전을 나타낸다.

- 상태 코드 및 설명 - 200 OK

  - 리퀘스트 처리 결과를 나타낸다.
  - 리퀘스트가 성공했는지 실패했는지 등을 나타내는 숫자 코드이다.

- 헤더 필드 - Date ~ Content-Type

<br>

## 상태를 유지하지 않는 프로토콜

- Stateless Protocol
  - HTTP는 Request와 Response를 교환하는 동안에 상태를 관리하지 않는다.
  - 따라서 과거 정보를 저장하고 있지 않다.  
    -> **범위성(Scalability)** 확보
    - 데이터를 매우 빠르고 확실하게 처리
    - 현재 Cookie라는 기술을 도입하여 해당 요구 사항을 충족

## Request URI로 리소스를 식별

- 인터넷 상의 리소스를 지정

### URI 지정 방법

http://hackr.jp/index.html을 리퀘스트하는 경우

- Request URI에 포함

  - `GET http://hackr.jp/index.html`

- Host 헤더 필드에 네트워크 로케이션을 포함
  - ```
    GET /index.html HTTP/1.1
    Host: hackr.jp
    ```

<br>

## 서버에 임무를 부여하는 HTTP 메소드

- 리소스에 어떠한 행동을 하기 원하는지를 지시하기 위해 존재한다.
- 대문자와 소문자를 구별하기 때문에 대문자로 기재해야한다.

### GET: 리소스 획득

- URI로 식별된 리소스를 가져오도록 요구한다.

- 리소스는 서버의 해석 결과이다.

- 텍스트면 그대로 반환, 프로그램이면 실행해서 출력된 내용을 반환한다.

<br>

### POST: 엔티티 전송

- 엔티티를 전송하기 위해 사용된다.

- 수신한 데이터의 처리된 결과를 반환한다.

<br>

### PUT: 파일 전송

- 파일을 전송하기 위해서 사용된다.

- 리퀘스트 중 포함된 엔티티를 URI로 지정한 곳에 보존하도록 요구

- 인증 기능이 없어서 보안의 문제로 웹사이트에선 사용하지 않는다.

- 상태 코드 204를 보편적으로 반환한다.

<br>

### HEAD: 메시지 헤더 취득

- GET과 같은 기능이지만 메시지 바디는 돌려주지 않는다.

- URI 유효성과 리소스 갱신 시간을 확인하는 목적 등으로 사용된다.

<br>

### DELETE: 파일 삭제

- 파일을 삭제하기 위해 사용된다.

- URI로 지정된 리소스의 삭제를 요구한다.

- PUT 메소드와 같이 인증 기능이 없어 일반적인 웹 사이트에서는  
  되지 않고 있다.

<br>

### OPTIONS: 제공하고 있는 메소드의 문의

- URI로 지정한 리소스가 제공하고 있는 메소드를 조사하기 위해 사용한다.

- Request

  ```
  OPTIONS * HTTP/1.1
  Host: www.hackr.jp
  ```

- Reponse
  ```
  HTTP /1.1 200 OK
  Allow: GET, POST, HEAD, OPTIONS
  (서버가 제공하고 있는 메소드를 되돌려준다.)
  ```

<br>

### TRACE: 경로 조사

- Web 서버에 접속해서 자신에게 통신을 되돌려 받는 루프백(loop-back)을 발생

- Request 보낼 때 "Max-Forwards"라는 헤더 필드에 수치를 포함시켜  
  서버를 통과할 때마다 그 수치를 줄여간다.

- 리퀘스트를 가장 마지막에 수신한 곳에서 상태 코드 200 OK를 반환한다.

- 프록시 등을 중계하여 오리진(origin) 서버에 접속할 때 그 동작을 확인하기 위해  
  사용되고 있다.

- 프록시 서버 등을 경유할 때 리퀘스트가 가공될 경우가 있다.

<br>

### CONNECT: 프록시에 터널링 요구

- 프록시에 터널 접속 확립을 요구하여 TCP 통신을 터널링 시키기 위해 사용된다.

- SSL, TLS(Transport Layer Security) 등의 프로토콜로 암호화된 것을
  터널링 시키기 위해 사용된다.

- `CONNECT 프록시 서버 : 포트 HTTP 버전`

- Request

  ```
  CONNECT proxy.hackr.jp:8080 HTTP /1.1
  Host: proxy.hackr.jp
  ```

- Response
  ```
  HTTP /1.1 200 OK (그 뒤에 터널링을 개시)
  ```

## 지속 연결

- 불필요하게 반복되는 TCP 연결/종료를 해결

- 어느 한 쪽이 명시적으로 연결을 종료하지 않는 이상 TCP 커넥션 연결을 계속 유지한다.

<br>

## 파이프라인화

- 리퀘스트 송신 후 리스폰스를 수신할 때까지 기다린 뒤에 리퀘스트를 발행하던 것을,  
  바로 다음 리퀘스트를 보낼 수 있다.

- 이는 지속 연결 보다 빠르다.

## 쿠키 - 상태 관리

- HTTP가 stateless protocol임에 의해 발생하는 문제를 해결하기 위한 시스템

- Request, Response에 쿠키 정보를 추가해서 클라이언트의 상태를 파악하기 위한  
  시스템이다.

- Response로 보내진 Set-Cookie라는 헤더 필드에 의해 쿠키를 클라이언트에 보존  
  하게 된다.

- 다음 번에 클라이언트가 같은 서버로 리퀘스트를 보낼 때, 자동으로 쿠키 값을 넣어서  
  송신한다.
