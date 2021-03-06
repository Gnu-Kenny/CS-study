# 네트워크 기본 지식

## **네트워크 구조**

- **네트워크** : 두 대 이상의 컴퓨터 간 연결

  - 네트워크를 통해 데이터를 서로 주고 받는다.

- **인터넷** : 전세계의 크고 작은 네트워크를 연결한 거대한 네트워크

- **패킷** : 네트워크를 통해 전송되는 데이터의 작은 조각

  - 원본 데이터가 너무 클 경우, 대역폭을 크게 차지해서 다른 패킷의 흐름을 막을 수 있음.

  - 따라서 패킷으로 *분할된 데이터를 복원하는 작업이 필요*함.
  - 복원을 위해 _각 패킷에 순서를 매겨_ 송신히 정렬이 가능하도록 해야함.

<br>

## **정보 단위**

### **비트와 바이트**

- **디지털 데이터(Digital Data)** : 0과 1의 집합

- **비트(Bit)** : 0과 1의 정보를 나타내는 최소 단위
  - 이를 네트워크에서 전송할 경우 전기적 신호로 인식한다.
- **바이트(Byte)** : 비트를 8개 모은 것

## **LAN과 WAN**

- **LAN** : 지리적으로 제한된 곳에서 사용하는 네트워크

- **WAN** : 지리적으로 넓은 범위에 구축된 네트워크

  - **인터넷 서비스 제공자(ISP)**가 제공하는 서비스를 통해 구축

- **인터넷 서비스 제공자(ISP)** : KT, U+, SK브로드밴드 등 인터넷 상용 서비스 사업을 하고 있는 사업자

<br>

|      |           LAN            |         WAN         |
| :--: | :----------------------: | :-----------------: |
| 범위 | 좁다(건물이나 특정 지역) | 넓다(랜과랜을 연결) |
| 속도 |          빠르다          |       느리다        |
| 오류 |           적다           |        많다         |

<br>

## **일반적인 네트워크 구성**

![회사 내 네트워크 구성](../images/company.png)

### **구성 요소**

- LAN

  - 유선 LAN
  - 무선 LAN

- 인터넷 서비스 제공자(ISP)

- 인터넷 회선

  - ex) 광 LAN

- 인터넷 공유기

  - ISP와 네트워크 연결

- DMZ
  - 외부에 공개하기 위한 네트워크
  - 소규모 회사에서의 네트워크 구성에 포함 (가정 내 x)
  - 외부 공개용 서버로 웹/DNS/메일 서버가 있다.
