## Multiple-Processor Scheduling

- CPU가 여러 개인 경우 스케줄링은 더욱 복잡해짐

- Homogeneous processor인 경우

  - Queue에 한줄로 세워서 각 프로세서가 알아서 꺼내가게 할 수 있다.

  - 반드시 특정 프로세서에서 수행되어야 하는 프로세스가 있는 경우에는 문제가 더 복잡해짐.

- Load sharing

  - 일부 프로세서에 job이 물리지 않도록 부하를 적절히 공유하는 메커니즘 필요

  - 별개의 큐를 두는 방법 vs 공동 큐를 사용하는 방법

- Symmetric Multiprocessing (SMP)

  - 각 프로세서가 각자 알아서 스케줄링 결정

- Asymmetric multiprocessing

  - 하나의 프로세서가 시스템 데이터의 접근과 공유를 책임지고 나머지 프로세서는 거기에 따름

## Real-Time Scheduling

- Hard real-time systems

  - Hard real-time task는 정해진 시간안에 반드시 끝내도록 스케줄링해야 함

- Soft real-time systems

  - Soft real-time task는 일반 프로세스에 비해 높은 priority를 갖도록 해야 함.

## Thread Scheduling

- Local Scheduling

  - User level thread의 경우 사용자 수준의 thread library에 의해 어떤 thread를 스케줄할지 결정

- Global Scheduling

  - Kernel level thread의 경우 일반 프로세스와 마찬 가지로 커널의 단기 스케줄러가 어떤 thread를 스케줄할지 결정

## Algorithm Evaluation

- 어떤 CPU 스케줄링 알고리즘이 좋은 알고리즘인가의 척도

- _Queueing models_

  - **확률 분포**로 주어지는 **arrival rate**와 **service rate** 등을 통해 각종 **performance index**값을 계산

- _Implementation (구현) & Measurement (성능 측정)_

  - **실제 시스템**에 알고리즘을 **구현**하여 실제 작업(**workload**)에 대해서 성능을 **측정** 비교

- _Simulation (모의 실험)_
  - 알고리즘을 **모의 프로그램**으로 작성 후 **trace**를 입력으로 하여 결과 비교
