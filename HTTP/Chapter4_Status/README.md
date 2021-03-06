# HTTP 상태 코드

## 상태 코드의 역할

- 서버로부터 리퀘스트 결과를 전달한다.

- 200 OK
  - 3자리 숫자와 설명으로 나타냄

**상태 코드 클래스**
| | 클래스 | 설명 |
| :--:| :--: | :--: |
| 1xx |Informational| 리퀘스트를 받아들여 처리중|
| 2xx | Success | 리퀘스트를 정상적으로 처리했음 |
| 3xx | Redirection |리퀘스트를 완료하기 위해서 추가 동작이 필요|
| 4xx | Client Error | 서버는 리퀘스트 이해 불가능 |
| 5xx | Server Error | 서버는 리퀘스트 처리 실패 |

<br>

## 2xx 성공(Success)

- 리퀘스트가 정상으로 처리 되었음.

### 204 No Content

- 리퀘스트를 받아서 처리 성공했지만 엔티티 바디를 포함하지 않는다.

- 클라이언트에 대해서 새로운 정보를 보낼 필요가 없는 경우 사용

<br>

### 206 Partial Content

- Range에 의해서 범위가 지정된 리퀘스트에 의해서 서버거 부분적 GET 리퀘스트를 받음

<br>

## 3xx 리다이렉트(Redirection)

- 정상적 리퀘스트 처리를 위해 브라우저 측에서 특정 처리가 필요함을 나타냄

### 301 Moved Permanently

- 디렉토리를 지정했을 때 마지막 부분에 슬래시( / ) 붙이는 것을 잊은 경우 등에 사용  
   `http://example.com/sample`
- 리퀘스트된 리소스에는 새로운 URI가 부여되어 있기 때문에, 이후로는 그 리소스를 참조하는
  URI를 사용해야 한다는 것을 나타냄

<br>

### 302 Found

- 리퀘스트된 리소스에는 새로운 URI가 부여되어 있기 때문에, 이후로는 그 리소스를 참조하는
  URI를 참조해 주길 바란다는 의믜

- 일시적 이동이라는 점이 301과의 차이점이다.

<br>

### 303 See Other

- 리퀘스트에 대한 리소스는 다른 URI에 있기 때문에 GET 메소드를 사용해서 얻어야 한다는 것을 나타냄

- POST 메소드로 액세스한 CGI 프로그램을 실행한 후에 처리 결과를 별도의 URI에 GET  
  메소드로 리다이렉트 시키고 싶은 경우에 사용

<br>

### 304 Not Modified

- 조건부 리퀘스트를 했을 때 리소스에 대한 액세스는 허락하지만, 조건이 충족되지 않음을 표시

- 리스폰스 바디에 어떤 것도 포함되어 있어서는 안된다.

- 3xx에 분류되어 있지만 리다이렉트와는 관계가 없다.

<br>

### 307 Temporary Redirect

- 302 Found와 같은 의미를 지니지만, POST로부터 GET으로 치환이 금지되어 있음에도 구현상 그와 같이 되어 있다.

- 브라우저 사양에 따라 POST에서 GET으로 치환을 하지 않는다.

<br>

## 4xx 클라이언트 에러(Client Error)

- 클라이언트 원인으로 에러가 발생했음을 나타낸다.

### 400 Bad Request

- 리퀘스트 구문이 잘못되었음을 나타낸다.

- 리퀘스트 내용을 재검토하고 나서 재송신할 필요가 있다.

<br>

### 401 Unauthorized

- 송신한 리퀘스트에 HTTP 인증 정보가 필요하다는 것을 나타낸다.

- 리소스에 적용되는 challenge를 포함한 WWW-Authenticate 헤더 필드를 포함할 필요가 있다.

<br>

### 403 Forbidden

- 리퀘스트된 리소스의 액세스가 거부되었음을 나타낸다.

- 거부의 이유를 명확하게 하는 경우에는 엔티티 바디에 기재해서 유저 측에 표시한다.

- 발생 원인
  - 파일 시스템의 퍼미션이 부여되지 않은 경우
  - 액세스 권한에 문제(허가되지 않은 송신 IP 주소의 액세스)가 있는 경우

<br>

## 5xx 서버 에러(Server Error)

- 서버의 원인으로 에러가 발생하고 있음을 나타낸다.

### 500 Internal Server Error

- 리퀘스트 처리 도중 에러가 발생하였음을 나타내고 있다.

- 웹 애플리케이션에 에러가 발생한 경우

<br>

### 503 Server Unavaliable

- 일시적으로 서버가 과부하 상태이거나 점검중이라 리퀘스트 처리가 현재 불가능함을 나타낸다.

- 상태가 해소되기까지 시간이 걸리는 경우 Retry-After 헤더 필드에 따라 클라이언트에 전달하는 것이 바람직하다.
