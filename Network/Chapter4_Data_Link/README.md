# 4. 데이터 링크 계층 : 랜에서 데이터 전송하기

## 이더넷

- 랜에서 데이터를 주고받는 규칙

### 데이터 링크 계층

- 네트워크 장비 간에 신호를 주고받는 규칙을 정한다
  - 랜에서 데이터를 주고받기 위해 필요하다.

<br>

### 규칙(이더넷)이 필요한 이유

- 허브에 의해 다른 컴퓨터에 데이터가 보이는 것을 방지하기 위함  
  -> 보내려는 데이터에 목적지 정보를 추가한다
- 여러 컴퓨터가 동시에 데이터 보낼 때 발생하는 충돌을 피하기 위함  
  -> CSMA/CD를 이용, 데이터를 보내는 시점을 늦춘다.

<br>

### CSMA/CD

- CS : 데이터를 보내려는 컴퓨터가 케이블에 신호가 흐르는지를 확인한다
- MA : 케이블에 데이터가 흐르지 않는다면 데이터를 보낸다
- CD : 충돌이 발생하고 있는지를 확인한다

<br>

## MAC 주소 (물리 주소)

- 랜 카드에 할당된 전 세계에서 유일한 번호
- 데이터 링크 계층(TCP/IP의 네트워크 계층)의 프레임-이더넷 헤더에 포함된다.

### MAC (Media Access Control)

- 랜 카드를 만든 제조사 번호 24비트 + 제조사가 붙인 일련번호 24비트로 구성

<br>

### 프레임

- 데이터 + 이더넷 헤더 + 트레일러
- 송신 시 캡슐화가 일어나며, 데이터 링크 계층에서 프레임을 만들고 물리 계층에서 프레임을 전기 신호로 전환하여 네트워크를 통해 전송한다.

- 이더넷 헤더

  - 목적지 MAC 주소 + 출발지 MAC 주소 + 유형
    - 유형  
      : 이더넷을로 전송되는 상위 계층 프로토콜의 종류을 식별하는 번호

- 트레일러(FCS: Frame Check Squence)

  - 데이터 전송 도중 오류가 발생하는지 확인하는 용도

<br>

### 수신

- 수신 컴퓨터는 목적지 MAC 주소가 자신의 MAC 주소와 같을 때만 역캡슐화 후 데이터를 수신한다.
- 역캡슐화 (수신 컴퓨터의 데이터 링크 계층 : 이더넷 헤더와 트레일러 분리 )
- 동시에 여러 데이터가 수신 될 때는 CSMA/CD 규칙을 사용

<br>

## MAC 주소 테이블 (MAC address table)

- 스위치의 포트 번호와 해당 포트에 연결된 컴퓨터의 MAC 주소가 저장되는 데이터베이스

### 스위치 (= 레이어 2 스위치 = 스위칭 허브)

- 허브와 달리 데이터 충돌이 발생하지 않는다

### MAC 주소 학습 기능

- 프레임이 전송시, 출발지 MAC 주소가 없으면 MAC 주소 테이블을 이용해 MAC주소를 포트와 함께 등록하는 기능

<br>

### 플러딩 (flooding)

- 목적지 MAC 주소가 MAC 주소 테이블에 없는 경우, 송신 포트 이외의 모든 컴퓨터에 데이터(프레임)이 전송되는 것

<br>

### MAC 주소 필터링

- 목적지 MAC 주소를 기준으로 목적지를 선택하는 것
- 불필요한 데이터를 네트워크에 전송하지 않도록 만든다

<br>

## 데이터가 케이블에서 충돌하지 않는 경우

- 효율 문제로 허브보다 스위치를 주로 사용한다.

### **통신 방식**

---

### 전이중 통신 방식

- 데이터의 송수신을 동시에 통신한다
- 데이터의 충돌이 발생하지 않기 때문에, 컴퓨터를 랜 케이블로 직접 연결할 때 사용한다.
- 스위치에서 사용한다.

<br>

### 반이중 통신 방식

- 회선 하나로 송신 수신을 번갈아 통신한다
- 데이터 동시에 전송하면 충돌 발생
- 허브에서 사용한다.

<br>

### **충돌 도메인 (collision domain)**

- 충돌이 발생할 때 영향이 미치는 범위. 넓을 수록 네트워크가 지연된다.
- 허브는 모든 컴퓨터에 충돌의 영향이 미치기에, 충돌 도메인의 범위가 넓다
- 스위치는 전이중 통신 방식이기에 충돌 도메인의 범위가 좁다

<br>

## ARP 주소

- 목적지 컴퓨터의 IP 주소를 이용, MAC 주소를 찾는 프로토콜

- 출발지 컴퓨터는 ARP 요청과 응답을 이용, MAC 주소를 얻고 이더넷 프레임을 만든다.

### ARP 요청(request)

- 목적지 컴퓨터의 MAC 주소를 모를 때 수행하는 네트워크 브로드캐스트

<br>

### ARP 응답(response)

- 요청에 대해 지정된 IP 주소를 가진 컴퓨터가 MAC 주소를 응답으로 보내는 것

<br>

### ARP 테이블

- 출발지 컴퓨터가 MAC 주소와 IP 주소의 매핑 정보를 보관하는 메모리.
- 보존 기간을 ARP 캐시로 지정, 일정 시간이 지나면 해당 정보를 삭제하고 다시 ARP 요청을 한다.

## 이더넷

- 이더넷은 케이블 종류와 통신 속도에 따라 다양한 규격으로 분류된다.

### Ex. 10BASE-T

- 10 : 통신 속도
- BASE : 전송 방식. BASE의 경우, BASEBAND를 의미
- T : 케이블 종류. UTP 케이블을 의미한다.

UTP 케이블만 케이블 종류를 표시하며, 동축 케이블의 경우 하이픈 없이 케이블 길이를 표시한다.