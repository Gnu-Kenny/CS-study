# 프로세스 동기화

## 데이터 접근

- 연산 공간과 저장 공간을 분리한다.

- Storage(저장 공간) -> Memory Address Space

- Execution(연산 공간) -> CPU Process

## Race Condition

- S-box(Storage)를 공유하는 E-box(Execution)가 여럿 있는 경우 Race Condition 가능성 있음.

## OS에서 race condition 발생 원인

1. kernel 수행 중 인터럽트 발생시

2. Process가 system call을 하여 kernel mode로 수행 중인데 context switch가 일어나는 경우

3. Multiprocessor에서 shared memory 내의 kernel data

### 인터럽트 발생

- 커널 모드 running 중 인터럽트 발생하여 인터러브 처리 루틴이 수행  
  -> 양쪽 다 커널 코드이므로 kernel address space 공유

### kernel mode

- user mode와 달리 kernel mode 사용시 주소 공간을 공유한다.

- kernel data를 읽어 들여 count ++ 하다 context switch가 일어난 상황

- 해결책
  - 커널 모드에서 수행 중일 때는 CPU를 preempt하지 않음
  - 커널 모드에서 사용자 모드로 돌아갈 때 preempt

### multiprocessor

- 어떤 CPU가 마지막으로 count를 store했는가? -> race condition  
  multiprocessor의 경우 interrupt enable/disable로 해결되지 않음

(방법 1) 한번에 하나의 CPU만이 커널에 들어갈 수 있게 하는 방법

- 운영체제 전체를 lock -> 비효율적

(방법 2) 커널 내부에 있는 각 공유 데이터에 접근할 떄마다 그 데이터에 대한 lock/ unlock을 하는 방법

## Process Synchronization 문제

- 공유 데이터(shared data)의 동시 접근(concurrent access)은 데이터의 불일치 문제(inconsistency)를 발생시킬 수 있다.

- 일관성(consistency) 유지를 위해서는 협력 프로세스(cooperating process) 간의 실행 순서(orderly execution)를 정해주는 메커니즘 필요

- Race condition

  - 여러 프로세스들이 동시에 공유 데이터를 접근하는 상황

  - 데이터의 최종 연산 결과는 마지막에 그 데이터를 다룬 프로세스에 따라 달라짐

- race condition을 막기 위해서는 concurrent process는 동기화(synchronize)되어야 한다.

## The Critical-Section Problem

- n개의 프로세스가 공유 데이터를 동시에 사용하기를 원하는 경우

- 각 프로세스의 code segment에는 공유 데이터를 접근하는 코드인 critical section이 존재

- problem
  - 하나의 프로세스가 critical section에 있을 때 다른 모든 프로세스는 critical section에 들어갈 수 없어야 한다.

## Initial Attempts to Solve Problem

- 두 개의 프로세스가 있다고 가정 P0, P1

- 프로세스들의 일반적인 구조

```c
do{
    entry section
    critical section
    exit section
    remainder section
}while (1);

```

- 프로세스들은 수행의 동기화(synchronize)를 위해 몇몇 변수를 공유할 수 있다. -> synchronization variable

## The Critical-Section Problem

- n 개의 프로세스가 공유 데이털르 동시에 사용하기를 원하는 경우

- 각 프로세스의 code segment에는 공유 데이터를 접근하는 코드인 critical section이 존재

- problem
  - 하나의 프로세스가 critical section에 있을 때 다른 모든 프로세스는 critical section에 들어갈 수 없어야 한다.

## Algorithm 1

- Synchronization variable

  ```c
  int turn;
  initially turn = 0; // -> P1 can enter its critical section if (turn == i)
  ```

- Process P2

  ```c
  do{
      while(turn != 0);   // My turn? 내차례가 아니라면 loop
      critical section
      turn = 1;           // Now it's your turn
      remainder section

  } while(1);
  ```

## 프로그램적 해결법의 충족 조건

Mutual Exclusion (상호 배제)

- 프로세스 Pi가 Critical section 부분을 수행 중이면 다른 모든 프로세스들은 그들의 critical section에 들어가면 안된다.

Progress (진행)

- 아무도 critical section에 있지 않은 상태에서 critical section에 들어가고자 하는 프로세스가 있으면 critical section에 들어가게 해주어야 한다.

Bounded Waiting (유한대기)

- 기다리는 시간이 유한해야한다.

- starvation을 막아야한다. - 특정 프로세스가 영원이 자원을 사용할 수 없는 문제

## Algorithm 2

- Synchronization variables

```c
boolean flag[2];
initially flag[모두] = false; // no one is in CS
Pi ready to enter its critical section if ( flag[i] == true))
```

- Process Pi

```c
do{
    flag[i] = true;  // Pretend I am in
    while (flag[i]); // Is he also in? then wait
    critical section
    flag[i] = false; // I am out now
    remainder section
}while(1);
```

- 둘다 2행까지 수행 후 끊임 없이 양보하는 상황 발생 가능

## Algorithm 3 (Peterson's Algorithm)

```c
do{
    flag[i]=true; // My intention is to enter
    turn = j;       // Set to his turn
    while(flag[i] && turn == j);    // wait only if ... 상대방이 깃발을 들고 상대방 차례인지 확인
    critical section
    flag[i] = false;
    remainder section
}while(1);
```

- Busy Waiting = Spin lock! (계속 CPU와 memory를 쓰면서 wait)

## ✅ Semaphores

- 앞의 방식들을 추상화시킴

- Semaphore S (S -> 자원의 수)

  - integer variable

  - 아래의 두 가지 atomic 연산에 의해서만 접근 가능

  P연산 (자원 획득 과정)

  ```c
  P(S): while(S < 0) do no-op;
        S--;
  ```

  V연산 (자원 반납 과정)

  ```c
  V(S):
        S++;
  ```
