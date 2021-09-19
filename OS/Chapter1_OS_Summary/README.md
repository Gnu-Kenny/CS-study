# 운영체제란?

![OS_table](../images/OS_table.png)

- 하드웨어 바로 위 S/W 계층

- 다른 모든 S/W와 하드웨어를 연결

- 편리한 환경 제공

  - 프로그램들이 독자적으로 PC에서 실해되는 느낌을 부여

  - 하드웨어를 직접 다루는 복잡한 부분을 대행

- **자원의 효율적 관리**

  - CPU, Memory, I/O 장치 등의 효율적 관리

  - **효율성**  
    -> 주어진 자원의 최대 성능

  - **형평성**  
    -> 특정 프로그램의 지나친 불이익 방지

<br>

## **컴퓨터 내부 구조**

### **CPU 역할**

![OS_table](../images/process_status.png)

<br>

### **CPU 스케줄링**

---

- 여러 프로그램들이 CPU 큐에서 대기중일때 어떤 프로그램에 CPU를 할당시킬지 정함

- **FCFS(First Come First Served)**  
  P1 = 24  
  P2 = 4  
  P3 = 2  
  process 도착 순서: P1, P2, P3

  - Wait Time: P1 = 0, P2 = 24, P3 = 27
  - Average waiting time = (0 + 24 + 27)/3 = 17

- **SJF(Shortest Job First)**  
  **CPU 사용시간**이 **가장 짧은 프로세스**를 제일 먼저 스케줄  
  -> **최소 평균 대기시간**(Minimum Average Waiting Time) 보장  
  P1 = 24
  P2 = 4  
  P3 = 2  
  process 도착 순서: P3, P2, P1

  - Wait Time: P3 = 0, P2 = 2, P1 = 6
  - Average waiting time = (0 + 2 + 6)/3 = 2.33..

  ❗️issue : 기아현상(Starvation) -> 형평성 문제

- **Round Robin**

  - 각 process는 동일 크기의 CPU 할당 시간을 가짐

  - 할당 시간 끝 -> 인터럽트 -> CPU 빼앗김 -> 큐 제일 뒤에 줄섬

  - n개의 process가 CPU 큐에 있는 경우  
    -> 어떤 process도 **(n-1) \* 할당시간** 이상 기다리지 않음

<br>

### **메모리 관리**

---

![memory_management](../images/memory_management.png)

- **LRU vs LFU**  
  CPU가 요청한 페이지 순서  
  1,1,1,1,2,2,3,3,2,4,5...

  ![memory_management](../images/page.png)

  5번 페이지를 보관하기 위해 삭제해야할 페이지는?

  - **LRU**(가장 오래전에 참조한 페이지 삭제): 1번

  - **LFU**(참조 횟수가 가장 적인 페이지 삭제): 4번

<br>

### **디스크 스케줄링**

---

### 디스크 접근 시간(Access Time)의 구성

- **탐색시간 (Seek Time)**

  - 헤드를 해당 트랙으로 움직이는데 걸리는 시간

- **회전 지연시간**
  - 헤드가 원하는 섹터에 도달하기까지 걸리는 시간
- **전송 시간**
  - 실제 데이터 전송 시간

<br>

### 디스크 스케줄링

- **FCFS(First Come First Served)**

  - Seek Time을 최소화하는 것이 목표
  - Seek Distance와 흡사

- **SSTF(Shortest Seek Time First)**

  - 시작점에서 탐색 시간이 가장 짧은 프로세스부터 처리
  - ❗️Issue: Starvation

- **SCAN**
  헤드가 한쪽 끝 -> 다른 한쪽 끝까지 이동 간 길목에 있는 모든 요청처리

<br>

### **저장 장치 계층 구조와 캐싱**

---

![memory_management](../images/cache.png)

<br>

<br>

## 운영체제 종류

- 서버용, PC용, 스마트디바이스용 OS

- 공개 소프트웨어(Open Source Software)
  - Linux, Android ...

### 커널 (좁은 의미)

- 메모리에 상주하는 운영체제의 핵심 부분

<br>

### 운영체제 (넓은 의미)

- 커널 뿐 아니라 각종 주변 시스템 유틸리티를 포함한 개념

<br>

## 운영체제의 분류

### **동시 작업 가능 여부**

- 단일 작업 (single tasking)
  - 한 번에 하나의 작업만 처리
- 다중 작업 (multi tasking)
  - 동시에 두 개 이상의 작업 처리

<br>

### **사용자의 수**

- 단일 사용자(single user)
  - MS-DOS, MS Windows
- 다중 사용자(multi user)
  - UNIX, NT server

<br>

### **처리 방식**

- 일괄 처리(batch processing)

  - 내가 편한대로 하겠다.
  - 작업 요청의 일정량을 모아서 한꺼번에 처리
  - 작업이 완전 종료될 때까지 기다려야함

- 시분할(time sharing)

  - 시간을 분할해서 쓴다.
  - 컴퓨터 연산을 일정한 시간 단위로 분할
  - interactive한 방식
  - 범용 컴퓨터

- 실시간(Realtime OS)

  - 정해진 시간 안에 어떠한 일이 반드시 종료됨이 보장

  - 개념확장
    - Hard realtime system
    - Soft realtime system - ex) 영상 디코딩

<br>

### 운영체제의 예

**유닉스(UNIX)**  
-> 여러 사용자나 여러 프로그램의 동시실행을 위해 개발됨

- 코드 대부분을 C언어로 작성
- 높은 이식성
- 최소한의 커널 구조
- 확장 용이
- 소스 코드 공개
- 프로그램 개발 용이

<br>

**DOS(Disk Operating System)**  
-> 단일 사용자를 위해 개발됨

- 메모리 관리 능력의 한계

<br>

**MS Window**

- MS사의 다중 작업용 GUI 기반 OS

- Plug and Play, 네트워크 환경 강화

- 기존의 DOS 응용 프로그램과의 호환성
