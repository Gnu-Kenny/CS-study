# HTTP 헤더

## 6.1 HTTP 메시지 헤더

- 클라이언트나 서버가 리퀘스트나 리스폰스를 처리하기 위한 정보가 들어 있다.

### 리퀘스트의 HTTP 메세지

- 메소드, URI, HTTP 버전, HTTP 헤더 필드 등으로 구성되어 있다.

<br>

### 리스폰스의 HTTP 메시지

- HTTP 메시지와 HTTP 버전, 상태 코드(코드와 설명), HTTP 헤더 필드 등으로 구성

<br>

## 6.2 헤더 필드

### 6.2.1 HTTP 헤더 필드는 중요한 정보를 전달한다.

- 부가적으로 중요한 정보를 전달하는 역할을 담당하고 있다.

- 메시지 바디의 크기나 사용하고 있는 언어, 인증 정보 등을 브라우저나 서버에 제공하기 위해 사용되고 있다.

<br>

### 6.2.2 HTTP 헤더 필드의 구조

- 헤더 필드 명과 필드 값으로 구성되어 있고 콜론 ":"으로 나뉘어져 있다.  
   `헤더 필드 명 : 필드 값`

- 예시: 메시지 바디의 오브젝트의 타입을 가리키는 Content-Type이라는 HTTP 헤더 필드가 포함되어 있다.  
   `Content-Type:text/html`

  - 헤더 필드 명 : Content-Type
  - 필드 값 : text/html

- 하나의 HTTP 헤더 필드가 여러 개의 필드 값을 가질 수 있다.  
   `Keep-Alive:timeout=15, max=100`

<br>

### 6.2.3 4종류의 HTTP 헤더 필드

- 일반적 헤더 필드(General Header Fields)

  - 리퀘스트 메시지와 리스폰스 메시지 둘 다 사용되는 헤더이다.

- 리퀘스트 헤더 필드(Request Header Fields)
  - 서버 측으로 송신된 리퀘스트 메시지에 사용되는 헤더이다
  - 리퀘스트의 부가적 정보와 클라이언트의 정보, 리스폰스의 콘텐츠에 관한 우선 순위 등을 부가한다.
- 리스폰스 헤더 필드(Response Header Fields)

  - 리스폰스 메시지에 사용되는 헤더이다.
  - 리스폰스의 정보와 서버의 정보, 클라이언트의 추가 정보 요구 등을 부가한다.

- 엔티티 헤더 필드(Entity Header Fields)
  - 리퀘스트, 리스폰스 메시지에 포함된 엔티티에 사용되는 헤더로 콘텐츠 갱신 시간 등의 엔티티에 관한 정보를 부가한다.

<br>

### 6.2.4 HTTP/1.1 헤더 필드 일람

- 헤드 필드에는 47 종류가 있다.

<br>

### 6.2.5 HTTP/1.1 이외의 헤더 필드

<br>

### 6.2.6 End-to-end 헤더와 Hop-by-hop 헤더

- HTTP 헤더 필드는 캐시와 비캐시 프록시의 동작을 정의하기 위해서 두 가지 카테고리로 분류되어 있다.

- End-to-end 헤더

  - 리퀘스트나 리스폰스의 최종 수신자에게 전송된다.
  - 캐시에서 구축된 리스폰스 중 보존되야 하고, 다시 전송되지 않으면 안되도록 되어있다.

- Hop-by-hop 헤더

  - 한 번 전송에 대해서만 유효하고 캐시와 프록시에 의해서 전송되지 않는 것도 있다.
  - HTTP/1.1 이후 사용되는 Hop-by-hop 헤더는 Connection 헤더 필드에 열거해야 한다.

- hop-by-hop 헤더에는 8개의 헤더 필드가 있고 이 이외의 헤더 필드는 모두 End-by-end 헤더로 분류된다.

  - **Connection**

  - **Keep-Alive**

  - **Proxy-Authenticate**

  - **Proxy-Authorization**

  - **Trailer**

  - **TE**

  - **Transfer-Encoding**

  - **Upgrade**

<br>

## 6.3 HTTP/1.1 일반 헤더 필드

- request/response 메세지 양쪽에서 사용되는 헤더

### 6.3.1 Cache-Control

- 디렉티브로 불리는 명령으로 캐싱 동작을 지정한다.

- 여러 개의 디렉티브를 지정하는 경우 콤마 ','로 구분

  - `Cache-Control: private, max-age=0, no-cache`

- Cache-Control 디렉티브 일람

  - 사용가능 디렉티브를 request/response로 나누어 나타낸다.
  - 캐시 리퀘스트 디렉티브

  |      디렉티브       | 파라미터  |                         설명                         |
  | :-----------------: | :-------: | :--------------------------------------------------: |
  |      no-cache       |   없음    |            오리진 서버에 강제적인 재검증             |
  |      no-store       |   없음    | 캐시는 리퀘스트, 리스폰스의 일부분을 보존해서는 안됨 |
  |   max-age = [초]    |   필수    |                리스폰스의 초대 age 값                |
  | max-state( = [초] ) | 생략 가능 |             기한이 지난 리스폰스를 수선              |
  |  min-fresh = [초]   |   필수    |      지정한 시간 이후에 변경된 리스폰스를 보냄       |
  |    no-transform     |   없음    |        프록시는 미디어 타입을 변환해서는 안됨        |
  |   only-if-cached    |   없음    |                캐시에서 리소스를 취득                |
  |   cache-extension   |     -     |            새로운 디렉티브를 위해서 토큰             |

  - 캐시 리스폰스 디렉티브

  |     디렉티브     | 파라미터  |                                설명                                |
  | :--------------: | :-------: | :----------------------------------------------------------------: |
  |      public      |   없음    |                  어딘가에 ㅣㄹ스폰스 캐시가 가능                   |
  |     private      | 생략 가능 |                   특정 유저에 대해서만 리스폰스                    |
  |     no-cache     | 생략 가능 |           유효성의 재확인 없이는 캐시는 사용해서는 안됨            |
  |     no-store     |   없음    |        캐시는 리퀘스트, 리스폰스의 일부분을 보존해서는 안됨        |
  |   no-transform   |   없음    |               프록시는 미디어 타입을 변경해서는 안됨               |
  | must-revalidate  |   없음    |        캐시 가능하지만 오리진 서버에 리소스의 재확인을 요구        |
  | proxy-revalidate |   없음    | 중간 캐시 서버에 대해서 캐시했던 리스폰스의 유효성의 재확인을 요구 |
  |  max-age = [초]  |   필수    |                       리스폰스의 최대 Age 값                       |
  | s-maxage = [초]  |   필수    |               공유 캐시 서버의 리스폰스 최대 Age 값                |
  | cache-exgtension |     -     |                    새로운 디렉티브를 위한 토큰                     |

<br>

### 캐시가 가능한지 여부를 나타내는 디렉티브

---

**public 디렉티브**

`Cache-control: public`

- 다른 유저에게도 돌려줄 수 있는 캐시를 해도 좋다는 것을 명시적으로 나타낸다.

**private 디렉티브**

`Cache-Control: private`

- response는 특정 유저만을 대상으로 한다.

- 특정 유저를 위해 리소스를 캐시할 수 있지만, 다른 유저로부터 같은 리퀘스트가 온다고 하더라도 그 캐시를 반환하지 않도록 한다.

**no-cache 디렉티브**

- `Cache-Control: no-cache`  
  캐시로부터 오래된 리소스가 반환되는 것을 막기 위해 사용

- `Cache-Control: no-cache=Location`  
  지정된 헤더 필드 이외에는 캐시하는 것이 가능하다.

<br>

### 캐시로 보존 가능한 것을 제어하는 디렉티브

**no-store 디렉티브**

- `Cache-Control: no-store`

request 혹은 response에 기밀 정보가 포함되어 있음을 나타낸다.

<br>

### 캐시 기한이나 검증을 지정하는 디렉티브

**s-maxage 디렉티브**

- `Cache-Control: s-maxage=604800 (단위 : 초)`

max-age와 기능이 동일하나 이는 여러 유저가 이용 할 수 있는 공유 캐시 서버에서만 적용된다.

<br>

**max-age 디렉티브**

- `Cache-Control: max-age=604800 (단위 : 초)`

  - 지정되었던 값보다 새로운 경우에는 캐시되었던 리소스를 받아들일 수 있다.

  - 지정된 값이 0이면 캐시 서버는 리퀘스트를 항상 오리진 서버에 넘길 필요가 있다.

<br>

**min-fresh 디렉티브**

- `Cache-Control: min-fresh=60 (단위 : 초)`

  - 적어도 지정된 시간은 최신 상태의 것을반환하도록 캐시 서버에 요구

**max-stale 디렉티브**

- `Cache-Control: max-stale=3600 (단위 : 초)`

  - 캐시된 리소스의 유효 기한이 끝났더라도 받아들일 수 있다.

  - 디렉티브에 값이 저장되있지 않은 경우 아무리 시간이 경과했더라도 리스폰스를 받아들인다.

**only-if-cached 디렉티브**

- `Cache-Control: only-if-cached `

  - 클라이언트는 캐시 서버에 대해서 목적한 리소스가 로컬 캐시에 있는 경우만 리소폰스 반환 요구한다.

  - 캐시 서버에서 리스폰스의 리로드와 유효성을 재확인하지 않도록 요구한다.

  - 캐시 서버가 로컬 캐시로부터 응답이 불가할 경우 504 gateway timeout 상태 반환

**must-revalidate 디렉티브**

- `Cache-Control: must-revalidate (단위 : 초)`

  - 리스폰스의 캐시가 현재도 유효한지 아닌지의 여부를 오리진 서버에 조회를 요구한다.

**proxy-revalidate 디렉티브**

- `Cache-Control: proxy-revalidate`

  - 모든 캐시 서버에 대해서 이후의 리퀘스트로 해당 리스폰스를 반환할 떄는 반드시 유효성 재확인을 하도록 요구

**no-transform 디렉티브**

- `Cache-Control: no-transform`

  - 리퀘스트와 리스폰스의 어느 쪽에 있어서도 캐시가 엔티티 바디의 미디어 타입을 변경하지 않도록 지정한다.
  - 캐시 서버 등에 의해서 이미지가 압축되는 것을 방지한다.

<br>

### Cache-Control 확장

**cache-extension 토큰**

- `Cache-Control: private, community = "UCI" `

  - community라는 디렉티브는 Cache-Control 헤더 필드에는 없지만 extension toekns에 의해서 추가할 수 있다.

  - extension tokens는 이해할 수 있는 캐시 서버에 대해서만 의미가 있다.

<br>

### 6.3.2 Connection

- 프록시에 더 이상 전송하지 않는 헤더 필드를 지정

- 지속적 접속 관리

**프록시에 더 이상 전송하지 않는 헤더 필드를 지정**

<br>

`Connection: 더 이상 전송하지 않는 헤더 필드 명`

- 프록시 서버에 더 이상 전송하지 않는 헤더 필드(hop-by-hop 헤더)를 지정할 수 있다.

<br>

**지속적 접속 관리**

`Connection: Close`

- 접속이 계속 유지되면서 추가 리퀘스트를 송신하도록 한다.

<br>

`Connection: Keep-Alive`

- HTTP/1.1 이전 버전의 HTTP에 경우, 지속적 접속이 디폴트가 아니었다. 이러한 경우 지속적 접속을 위해선 Keep-Alive라고 지정을 해야한다.

<br>

### 6.3.3 Date

- HTTP 메시지를 생성한 날짜를 나타낸다.

- `Date: Tue, 03 Jul 2012 04:40:59 GMT`

- `Date: Tue, 03-Jul-2012 04:40:59 GMT`
  - 오래된 버전의 HTTP에 경우 RFC850에 정의된 다음과 같은 포맷을 사용한다.

<br>

### 6.3.4 Pragma

- `Pragma: no-cache`

  - 일반 헤더 필드지만 클라이언트 리퀘스트에서만 사용한다.

  - 클라이언트는 캐시된 리소스의 리스폰스를 원하지 않음을 모든 중간 서버에 알리기 위해 사용한다.

<br>

### 6.3.5 Trailer

- 메세지 뒤에 기술된 헤더 필드를 미리 전달할 수 있다.

- 청크 전송 인코딩을 사용하는 경우 사용 가능하다.

```
... (메세지 바디) ...
0
Expires: Tue, 28 Sep 2004 23:59:59 GMT
```

<br>

### 6.3.6 Transfer-Encoding

- 메시지 바디의 전송 코딩 형식을 지원하는 경우 사용하게 됨

- HTTP/1.1에서 전송 코딩 형식으로 청크 전송만이 정의

`Transfer-Encoding: chunked`

- Transfer-Encoding 헤더 필드로 지정한 것처럼 청크 전송 코딩이 유효한 상태

- 3,312 bytes 912 bytes 청크 데이터로 분할되어 있는 것을 알 수 있음

<br>

### 6.3.7 Upgrade

- HTTP 및 다른 프로토콜의 새로운 버전이 통신에 이용되는 경우에 사용한다

- 지정 대상이 전혀 다른 통신 프로토콜이라고 해도 문제 없다.

- `양쪽 모두 Connection 헤더 필드가 지정되어있다.`

<br>

### 6.3.8 Via

- 리퀘스트 혹은 리스폰스 메시지의 경로를 알기 위해 사용한다.

- 프록시 혹은 게이트웨이는 자신의 서버 정보를 Via 헤더 필드에 추가한 뒤에 메시지를 전송한다.

- 이것은 traceroute와 메일의 Received 헤더의 기능과 유사하다.

- 전송된 메시지 추적과 리퀘스트 루프의 회피 등에 사용되기 때문에 `프록시 경유시 반드시 부가한다.`

<br>

### 6.3.9 Warning

- HTTP/1.0 response 헤더(Retry-After)가 HTTP/1.1에서 변경 된 것

- response에 관한 추가 정보를 전달

- 기본적으로 캐시에 관한 문제의 경고를 유저에 전달함

- Warning 헤더 형식

> Warning: [경고 코드][경고한 호스트:포트 번호]"[경고문]"([날짜])

| 코드 | 경고문                           | 설명                                                                                    |
| ---- | -------------------------------- | --------------------------------------------------------------------------------------- |
| 110  | Response is state                | 프록시가 유효기간이 지난 리소스를 반환                                                  |
| 111  | Revalidation failed              | 프록시가 리소스 유효성 재확인에 실패 <br/> (서버에 도달할 수 없는 등)                   |
| 112  | Disconnection operation          | 프록시가 네트워크로부터 고의로 끊겨 있음                                                |
| 113  | Heuristic expiration             | 리스폰스가 24시간 이상 경과하고 있는 경우 <br/> (캐시의 유효기간을 24시간 이상 설정 시) |
| 199  | Miscellaneous warning            | 임의의 경고문                                                                           |
| 214  | Transformation applied           | 프록시가 인코딩과 미디어 타입 등에 대응해서 <br/> 무언가의 처리를 한 경우               |
| 299  | Miscellaneous persistent warning | 임의의 경고문                                                                           |

<br>

## 6.4 리퀘스트 헤더 필드

- 클라이언트 측에서 서버 측으로 송신된 리퀘스트 메시지에 사용되는 헤더

- 리퀘스트의 부가 정보와 클라이언트의 정보, 리스폰스의 콘텐츠에 관한 우선 순위 등을 추가한다.

### 6.4.1 Accept

` Accept: text/html, application/xhtml+xml,application/xml;q=0.9.*/*;q=0.8`

- 유저 에이전트에 처리할 수 있는 미디어 타입과 미디어 타입의 상대적인 우선 순위를 전달하기 위해서 사용된다.

- 미디어 타입의 지정은 "타입/서브 타입"으로서 한번에 여러 번 설정할 수도 있다.

- 텍스트 파일

  - text/html, text/plain, text/css

  - application/xhtml+xml, application/xml ...

- 이미지 파일

  - image/jpeg, image/gif, image/png ...

- 동영상 파일
  - video/mpeg, video/quicktime ...
- 애플리케이션용 바이너리 파일
  - application/octet-stream, application/zip ...

<br>

### 6.4.2 Accept-Charset

`Accept-Charset:iso-8859-5, unicode-1-1:q+0.8`

- 유저 에이전트에서 처리할 수 있는 문자셋으로, 문자셋의 상대적인 우선 순위를 전달하기 위해 사용한다.

- 문자셋은 한번에 여러 개를 지정할 수 있다.

- 품질 지수에 의해 상대적으로 우선 순위를 표시한다. (Accept와 동일)

- 서버 구동형 네고시에이션에 이용한다.

<br>

### 6.4.3 Accept-Encoding

`Accept-Encoding: gzip, deflate`

- 유저 에이전트가 처리할 수 있는 콘텐츠 코딩과 콘텐츠 코딩의 상대적인 우선 순위를 전달하기 위해서 사용한다.

- 콘텐츠 코딩의 지정은 한번에 여러 개를 지정할 수 있다.

- gzip
  - 파일 압축 프로그램 gzip(GNU zip)에서 생성된 인코딩 포맷(RFC1952)으로 Lempel-Ziv 부호(LZ77)와 32비트 CRC를 사용
- compress
  - UNIX 파일 압축 프로그램 "compress"에 의해서 만들어진 인코딩 포맷으로 → Lempel-Ziv-Welch 부호(LZW)를 사용
- deflate
  - Zlib 포맷(RFC1950)과 deflate 압축 알고리즘(RFC1951)에 의해서 만들어진 인코딩 포맷을 조합한 것
- identity
  - 압축과 변형을 하지 않는 디폴트 인코딩 포맷

Accept 헤더 필드와 같이 품질지수에 의해서 상대적인 우선 순위를 표시함

- "\*"(에스터리스크)를 지정하면 와일드 카드로서 모든 인코딩 포맷을 가리킴

<br>

### 6.4.4 Accept-Language

`Accept-Language: ko-kr, en-us;q=0.7, en;q=0.3`

- 유저 에이전트가 처리할 수 있는 자연어의 세트(ko, en)

- 자연어 세트의 상대적인 우선 순위를 전달하기 위해서 사용

  - 자연어 세트 : 한번에 여러 개를 지정 가능

- 품질 지수에 의해 상대적인 우선 순위를 나타냄(Accept 헤더 필드와 같음)

  - ex 한국어 리소스가 있는 경우 → 한국어

  - 없으면 → 영어 리소스로 response를 받고 싶다는 것을 의미

<br>

### 6.4.5 Authorization

- 유저 에이전트의 인증 정보(크리덴셜 값)을 전달하기 위해서 사용

- 서버에 인증을 받으려 하는 유저 에이전트의 경우

  - 상태 코드 401 response 뒤에 request에 Authorization 헤더 필드를 포함

- 공유 캐시가 Authorization 헤더 필드를 포함하는 request를 받은 경우

<br>

### 6.4.6 Expect

`Expect: 100-continue`

- 클라이언트가 서버에 특정 동작 요구를 전달

- 기대하고 있는 요구에 서버가 응답하지 못해서 에러가 발생하는 경우

  - 상태 코드 417 Expectation Failed 반환

- 이 헤더 필드에 원하는 확장을 딸려 보낼 수 있지만 HTTP/1.1 사양에는 "100-continue"(상태코드 100 Continue의 의미만)가 정의 되어 있음

- 상태 코드 100 response를 가진 client
  - request할 때에 E`xpect : 100-continue`로 지정

<br>

### 6.4.7 From

`From: info@hackr.jp`

- 유저 에이전트를 사용하고 있는 유저의 메일 주소를 전달함

- 기본적으로 검색 엔진 등의 에이전트 책임자 이메일 에이전트 사용  
  → From 헤더 필드를 포함해야 함

<br>

### 6.4.8 Host

`Host: www.hackr.jp`

- request한 리소스의 인터넷 호스트와 인터넷 호스트와 포트 번호를 전달한다.

- HTTP/1.1 유일한 필수 헤더 필드

- 1대의 서버에서 복수의 도메인을 할당할 수 있는 가상 호스트의 구조와 연관있다.

  - 리퀘스트가 서버에 오면 호스트명 -> IP 주소로 해결

  - Host 헤더 필드에 리퀘스트를 받을 호스트명을 명확하게 한다.  
    `Host: `

<br>

### 6.4.9 If-Match

- `If-xxx' 와 같은 서식의 리퀘스트 헤더 필드는 `조건부 리퀘스트`로 불린다.

- 조건부 리퀘스트를 받은 서버는 지정된 조건에 맞는 경우에만 리퀘스트를 받는다.

`If-Match: "123456"`

- 조건부 리퀘스트의 하나로 서버 상의 리소스를 특정하기 위해 엔티티 태그(ETag) 값을 전달한다.

- 서버는 If-Match의 필드 값과 리소스의 ETag 값이 일치한 경우에만 리퀘스트를 받아들인다.

  - 불일치시 상태 코드 412 Precondition Failed 리스폰스를 반환한다.

- If-Match 필드 값에 "\*"를 지정할 수도 있다.
  - 이러한 경우 Etag 값과 상관없이 리소스가 존재한다면 리퀘스트를 처리한다.

<br>

### 6.4.10 If-Modified-Since

`If-Modified-Since: Thu, 15 Apr 2004 00:00:00 GMT`

- 조건부 리퀘스트의 하나로 갱신 날짜가 필드 값보다 새롭지 않다면  
  -> 리퀘스트를 받아들이겠다는 뜻을 전달

- 필드 값에 지정된 날짜 이후, 지정한 리소스가 갱신되어 있지 않은 경우  
  -> 상태 코드 304 Not Modified 리스폰스를 반환

<br>

### 6.4.11 If-None-Match

- 조건부 리퀘스트의 하나로 If-Match와 반대로 동작한다.

- If-None-Match의 필드 값에 지정된 ETag 값이 지정된 리소스의 ETag값과 일치하지 않으면  
  -> 리퀘스트를 받아들이겠다는 뜻을 전달한다.

<br>

### 6.4.12 If-Range

- 조건부 리퀘스트의 하나로 If-Range로 지정한 필드값(ETag 값, 혹은 날짜를 지정)과 지정한 리소스의 ETag 값 혹은 날짜가 일치하면  
  -> Range 리퀘스트로서 처리하고 싶다는 것을 전달한다.

  - 일치하지 않는 경우 리소스 전체를 반환한다.

<br>

### 6.4.13 If-Unmodified-Since

`If-Unmodified-Since: Thu, 03 Jul 2012 00:00:00 GMT`

- If-Modified-Since 헤더 필드와 반대로 동작한다.

- 지정된 리소스가 필드 값에 지정된 날짜 이후에 갱신되어 있지 않는 경우에만  
  -> 리퀘스트를 받아들이도록 전달한다.
  - 지정된 날짜 이후에 갱신된 경우 상태 코드 412 Precondition Failed 리스폰스를 반환한다.

<br>

### 6.4.14 Max-Forwards

`Max-Forwards: 10`

- TRACE 혹은 OPTIONS 메소드에 의한 리퀘스트를 할 때에 전송해도 좋은 서버 수의 최대치를 10진수 정수로 지정한다.

- 서버는 다음 리퀘스트를 전송할 때 Max-Forwards 값 - 1 로 다시 세트한다.

- Max-Forwards 값 = 0 인 리퀘스트를 받는 경우 전송 없이 리스폰스를 반환할 필요가 있다.

- 프록시 서버 등 여러 대의 서버를 경우 하는 경우
  - 도중에 리퀘스트 전송 실패하게 되면 클라이언트에는 리스폰스가 되돌아 오지 않기 떄문에 알 수 없다.

<br>

### 6.4.15 Proxy-Authorization

`Proxy-Authorization: Basic dGlwOjkpNLAGfFY5`

- 프록시 서버에서의 인증 요구를 받아들인 때에 인증에 필요한 클라이언트 정보를 전달한다.

- 클라이언트와 서버의 HTTP 액세스 인증과 다른 점

  - 클라이언트와 프록시 사이에 인증이 이루어진다.

  - 클라이언트 - 서버의 경우 Authorization 헤더 필드와 같은 역할을 한다.

<br>

### 6.4.16 Range

`Range: bytes=5001-10000`

- 리소스의 일부분만 취득하는 Range

- request를 할 때 지정 범위를 전달
- 위에 소개한 예에서는 5001 바이트부터 10000 바이트 까지 리소스를 요구 중
- Range 헤더 필드가 달린 request 받아들인 서버가 request 처리 가능  
  → 상태 코드 206 Partial Content response 반환
- Range request를 처리할 수 없는 경우
  - 상태 코드 200 OK와 함께 전체 리소스 반환

<br>

### 6.4.17 Refer

- Refer를 보려면 Request 중의 URI가 어느 웹 페이지로부터 발행되었는지 알 수 있음

- request가 발생한 본래 리소스의 URI를 전달

- 브라우저의 주소창에 직접 URI를 입력한 경우 보안상 문제가 될 경우 전달하지 않아도 된다.

- 본래 리소스의 URI의 쿼리에 ID 및 패스워드와 비밀 정보 포함인 경우

  - Refer를 통해서 다른 서버에 노출될 우려가 존재함

- Referrer가 맞지만 → 잘못된 철자로 사용 중

<br>

### 6.4.18 TE

`TE: gzip, deflate:q=0.5`

TE 헤더 필드 :

- response로 받을 수 있는 전송 코딩 형식

- 상대적인 우선 순위를 전달

- Accept-Encoding 헤더 필드와 매우 비슷

  - 전송 코딩이 적용

- 전송 코딩의 지정 이외에 Trailer를 동반하는 청크 전송 인코딩 형식 지정 가능

  - 필드 값에 "trailers"라고 기록

> TE: trailers

<br>

### 6.4.19 User-Agent

- request를 생성한 브라우저와 유저 에이전트의 이름 등을 전달하기 위해 사용
- 로봇 엔진의 request 경우에는 로봇 엔진의 책임자
- 메일 주소가 부가된 것도 있음
- 또는 프록시 경유로 리퀘스트의 경우에는 프록시 서버의 이름 등이 부가된 것도 있음

<br>

## 6.5 리스폰스 헤더 필드

- 리스폰스 메시지에 적용된 헤더

  - 리스폰스의 부가 정보
  - 서버의 정보
  - 클라이언트에 부가 정보 요구

### 6.5.1 Accept-Range

`Accept-Ranges: bytes`

- Range 리퀘스트를 접수할 수 있는지 여부 전달

- 지정 가능한 필드 값
  - 수신 가능한 경우 -> bytes
  - 수신 불가능한 경우 -> none

<br>

### 6.5.2 Age

`Age: 600`

- 오리진 서버에서 리스폰스가 생성된 시점 전달
  - 리스폰스한 서버가 캐시 서버  
    -> 캐시된 리스폰스가 다시 실증되었던 때부터 검증한 시간
  - 리스폰스한 서버가 프록시 -> Age 헤더 필드 필수

<br>

### 6.5.3 ETag

`ETag: "82e22293907ce725faf67773957acd12"`

- 엔티티 태그

- 일의적으로 리소스를 특정하기 위한 문자열을 전달

- 서버는 리소스마다 ETag 값 할당

- 리소스 갱신시 ETag 값도 갱신 필요

_강력한 ETag 값과 약한 ETag 값_

- 강한 ETag

  - 엔티티가 아주 조금 다르더라도 반드시 값 변화  
    `ETag: "Usagi-1235"`

- 약한 ETag 값
  - 리소스가 같다는 것만을 나타낸다.
  - 의미가 다른 리소스로 그 차이가 있는 경우에만 ETag 값이 변화
  - 값의 앞부분에 "W/"가 붙는다.  
    `ETag: W/"usagi-1234"`

<br>

### 6.5.4 Location

`Location: http://www.usagidesign.jp/sample.html`

- 리스폰스의 수신자에 대해 Request-URI 이외의 리소스 액세스를 유도하는 경우 사용

- "3xx: Redirection" 리스폰스에 대해 리다이렉트 처의 URI를 기술

- 해당 필드를 포한한 리스폰스를 받으면 강제로 리다이렉트 하는 곳의 리소스에 액세스 시도

<br>

### 6.5.5 Proxy-Authenticate

`Proxy-Authenticate: Basic realm="Usagidesign Auth"`

- 프록시 서버에서의 인증 요굴 ㄹ 클라이언트에 전달

- 클라이언트와 프록시 사이에서 인증이 이루어진다.  
  -> HTTP 액세스 인증과의 차이점

<br>

### 6.5.6 Retry-After

`Retry-After: 120`

- 클라이언트가 일정 시간 후에 리퀘스트를 다시 시행해야 하는지를 전달

- 상태 코드 503 Service Unavailable, 3xx Redirect 리스폰스와 주로 사용

- 값으로 *날짜*나 *리스폰스 이후의 몇 초*를 지정할 수 있다.

<br>

### 6.5.7 Server

`Server: Apache/2.2.17(Unix)`

- 서버에 설치되어 있는 HTTP 서버의 소프트웨어를 전달한다.

- 소프트웨어의 명칭과 함께, 버전이나 옵션에 대해서도 기재하는 경우가 있다.
  `Sever: Apache/2.2.6 (Unix) PHP/5.2.5`

<br>

### 6.5.8 Vary

`Vary: Accept-Language`

- 캐시를 컨트롤하기 위해 사용한다.

- 오리진 서버가 프록시 서버에 로컬 캐시를 사용하는 방법에 대한 지시를 전달한다.

- 같은 리소스에 대한 리퀘스트라도 Vary에 지정되었던 헤더 필드가 다른 경우 오리진 서버로 부터 리소스를 취득할 필요가 있다.

<br>

### 6.5.9 WWW-Authenticate

`WWW-Authenticate: Basic realm="Usagidesign Auth"`

- HTTP 액세스 인증에 사용

- Request-URI에 지정했던 리소스에 적용할 수 있는 인증 스키마와 파라미터를 나타내는 Challenge를 전달

- 401 Unauthorized 리스폰스에 반드시 포함된다.

- "realm"는 Request-URI에 지정된 리소스를 식별하기 위한 문자열이다.

<br>

## 6.6 엔티티 헤더 필드

- 리퀘스트/리스폰스 메시지에 포함된 엔티티에 사용되는 헤더

- 콘텐츠의 갱신 시간 같은 엔티티에 관한 정보를 포함한다.

### 6.6.1 Allow

`Allow: GET, HEAD`

- Request-URI에 지정된 리소스가 제공하는 메소드의 일람ㅇ르 전달한다.

- 서버가 받을 수 없는 메소드를 수신한 경우  
  -> 405 Method Not Allowed 리스폰스와 함께 수신 가능한 메소드 일람을 기술한 Allow 헤더 필드 반환

<br>

### 6.5.2 Content-Encoding

`Content-Encoding: gzip`

- 서버가 엔티티 바디에 대해서 실시한 콘텐츠 코딩 형식을 전달

- 콘텐츠 코딩은 엔티티의 정보가 누락되지 않도록 압축할 것을 지시
  - Gzip
  - Compress
  - Deflate
  - Identity

<br>

### 6.5.3 Content-Language

`Content-Language: en`

- 엔티티 바디에 사용된 자연어를 전달

<br>

### 6.6.4 Content-Length

`Content-Length: 15000`

- 엔티티 바디의 크기를 전달한다.

- 엔티티 바디에 전송 코딩이 실시된 경우 헤당 헤더 필드를 사용하면 안된다.

<br>

### 6.6.5 Content-Location

`Content-Location: http://www.hackr.jp/index-ja.html`

- 메시지 바디에 대응하는 URI 전달

- 메시지 바디로 반환된 리소스의 URI를 나타낸다.
  - Location 헤더 필드와의 차이점

<br>

### 6.6.6 Content-MD5

`Content-MD5: OGFkZDUwNGVhNGY3N2MxMDlwZmQ4NTBmY2lyTY==`

- 메시지 바디가 변경되지 않고 도착했는지 확인하기 위해 MD5 알고리즘에 의해 생성된 값을 전달한다.

- MD5에 의해 생성된 128비트 바이너리 값에 Base64 인코딩을 한 결과를 필드 값에 기록

  - HTTP 헤더에는 바이너리 값을 기록하는 것이 불가능하기 때문

- 유효성을 확인하기 위해서 수신한 클라이언트 측 메시지 바디에 같은 MD5 알고리즘 실행

<br>

### 6.6.7 Content-Range

`Content-Range: bytes 5001-10000/10000`

- Range 리퀘스트에 대해 리스폰스 할 때 사용한다.

- 리스폰스로 보낸 엔티티가 어느 부분에 해당하는 가를 전달한다.

- 필드 값에는 현재 보내고 있는 곳을 바이트로 지정한 범위와 전체 사이즈를 기록한다.

<br>

### 6.6.8 Content-Type

`Content-Type: text/html; charset=UTF-8`

- 엔티티 바디에 포함되는 오브젝트의 미디어 타입을 전달한다.

- "타입/서브 타입"으로 필드 값 기록한다.

- Charset 파라미터
  - iso-8859-1
  - euc-kr

<br>

### 6.6.9 Expires

`Expires: Wed, 04 Jul 2012 08:26:05 GMT`

- 리소스의 유효 기한 날짜를 전달한다.

- 캐시 서버가 해당 헤더 필드를 포함한 리소스 수신한 경우  
  -> 필드 값으로 지정된 날짜까지 리스폰스의 복사본을 유지하고 리퀘스트에는 캐시로 응답한다.

<br>

### 6.6.10 Last-Modified

`Last-Modified: Wed, 23 May 2012 09:59:55 GMT`

- 리소스가 마지막으로 갱신되었던 날짜 정보를 전달한다.

- Request-URI가 지정된 리소스가 갱신되었던 날짜가 된다.
  - CGI 등의 동적인 데이터를 다룰 경우 그 데이터의 최종 갱신 날짜가 되는 경우도 있다.

<br>

## 6.7 쿠키를 위한 헤더 필드

- 쿠키

  - 유저 식별과 상태 관리에 사용되는 있는 기능
  - 웹 사이트가 유저의 상태를 관리하기 위해 웹 브라우저 경유로 유저의 컴퓨터 상에 일시적으로 데이터를 기록해 둔다.
  - 다음에 그 유저가 웹 사이트에 액세스 해 왔을 때 지난번에 발행한 쿠키를 송신 받을 수 있다.

### 쿠키의 사양

1. 넷스케이프사에 의한 사양

- 쿠키를 고안한 넷스케이프 커뮤니케이션스 사의 사양

- 현재 널리 보급되어 있는 쿠키 방식의 근원

2. RFC2109

- 쿠키 사양의 표준화를 시험하기 위해 정리된 규격

- 현재 사용되지 않음.

3. RFC2965

- "Set-Cooke2"와 "Cookie2"라는 HTTP 헤더 필드를 정의했지만 실제로 거의 사용하지 않음.

4. RFC6265

- 넷스케이프사에 의한 사양을 디 펙토 스탠다드로서 쿠키의 사양을 재정의한 것

- `현재 가장 잘 사용되고 있는 쿠키 사양은 넷스케이프사의 사양을 근간으로 확장한 것이다.`

- 쿠키를 위한 헤더 필드

  | 헤더 필드 명 |              설명               | 헤더 종별 |
  | :----------: | :-----------------------------: | :-------: |
  |  Set-Cookie  | 상태 관리 개시를 위한 쿠키 정보 | 리스폰스  |
  |    Cookie    |    서버에서 수신한 쿠키 정보    | 리퀘스트  |

<br>

### 6.7.1 Set-Cookie

```
Set-Cookie: satus-enable; expires=Tue, 05 Jul 2011 07:26:31 GMT;=>path=/;domain=.hack.jp;
```

- 서버가 클라이언트에 대해 상태 관리를 시작할 때 다음과 같은 정보를 전달한다.

  |       속성       |                                          설명                                           |
  | :--------------: | :-------------------------------------------------------------------------------------: |
  |    NAME=VALUE    |                              쿠키에 부여된 이름과 값(필수)                              |
  |   Expires=DATE   |               쿠키 유효 기한(지정되지 않은 경우는 브라우저를 닫을 때까지)               |
  |    Path-PATH     | 쿠키 적용 대상이 되는 서버 상의 디렉토리(지정하지 않은 경우는 도큐먼트와 같은 디렉토리) |
  | Domain=도메인 명 |    쿠키 적용 대상이 되는 도메인 명(지정하지 않은 경우는 쿠키를 생성한 서버의 도메인)    |
  |      Secure      |                       HTTPS로 통신하고 있는 경우에만 쿠키를 송신                        |
  |     HttpOnly     |                     쿠키를 JavaScript에서 액세스하지 못하도록 제한                      |

<br>

### 6.7.2 Cookie

`Cookie: status=enable`

- Cookie 헤더 필드는 클라이언트가 HTTP의 상태 관리 지원을 원할 때 서버로부터 수신한 쿠키를 이후의 리퀘스트에 포함해서 전달한다.

- 쿠키를 여러 개 수신하고 있을 때에는 쿠키를 여러 개 보내는 것도 가능하다.

<br>

## 그 이외의 헤더 필드

- X-frame-Option

- X-XSS-Protection

- DNT

- P3P

### 6.8.1 X-frame-Option

`6.8.1 X-frame-Option: DENY`

- 다른 웹 사이트의 프레임에서 표시를 제어하는 HTTP 리스폰스 헤더

- 클릭 재킹(Click Jacking)을 막는 것을 목적으로 한다.

- 헤더에서 지정할 수 있는 값

  - DENY: 거부

  - SAMEORIGIN: Top-level-browsing-context가 일치한 경우에만 허가

- 모든 웹 서버에서 설정해두는 것이 바람직하다.

- apache2.conf의 설정 예

```
<IfModule mod_headers.c>
  Header append X-FRAME-OPTIONS"SAMEORIGIN"
<IfModule>
```

<br>

### 6.8.2 X-XSS-Protection

`X-XSS-Protection: 1`

- 크로스 사이트 스크립팅(XSS) 대책으로서 브라우저의 XSS 보호 기능을 제어하는 HTTP 리스폰스 헤더

- 헤더에서 지정할 수 있는 값

  - 0: XSS 필터를 무효로 한다.

  - 1: XSS 필터를 유효로 한다.

<br>

### 6.8.3 DNT

`DNT: 1`

- Do Not Track(DNT)라는 뜻이며 `개인 정보 수집을 거부하는 의사`를 나타내는 HTTP 리퀘스트 헤더이다.

- 타깃 광고 등에 이용되는 트래킹의 거부 의사를 나타내기 위한 방법 중 하나이다.

- 헤더에서 지정할 수 있는 값

  - 0: 트래킹 동의

  - 1: 트래킹 거부

- DNT 헤더 필드의 기능이 유효성을 유지하기 위해서는 웹 서버에서 DNT를 지원할 필요가 있다.

<br>

### 6.8.4 P3P

```
P#P: CP="CAO DSP LAW CURa ADMa DEVa TAAIa PSAa PSDa IVAa IVDa OUR BUS IND UNI COM NAV INT"
```

- 웹 사이트 상의 프라이버시 정책에 P3P(The Platform for Privacy Preferences)를 사용하는 것

- 프로그램이 읽을 수 있는 형태로 나타내기 위한 HTTP 리스폰스 헤더이다.

- P3P 설정 순서

  1. P3P 정책 작성

  2. P3P 정책 참조 파일을 작성해서 "/w3c/p3p.xml"에 배치

  3. P3P 정책으로부터 콤팩트 정책을 작성하고 HTTP 리스폰스 헤더에 출력
