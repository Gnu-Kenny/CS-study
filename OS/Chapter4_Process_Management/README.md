## 프로세스 생성(Process creation)

### 부모 프로세스(Parent process)가 자식 프로세스(children process) 생성

### 프로세스의 트리(계층 구조) 형성

### 프로세스는 자원을 필요로 함

- 운영체제로부터 받는다.

- 부모와 공유한다.

### 자원의 공유

- 부모와 자식이 모든 자원을 공유하는 모델

- 일부를 공유하는 모델

- 전혀 공유하지 않는 모델

### 수행(Excution)

- 부모와 자식은 공존하며 수행되는 모델
  - 전역 변수나 어디서 수행됐는지 위치까지 복사
- 자식이 종료(terminate)될 떄까지 부모가 기다리는(wait)모델

### 주소 공간(Address space)

- 자식은 부모의 공간을 복사함(binary and OS data)

- 자식은 그 공간에 새로운 프로그램을 올림

### 유닉스의 예

- **fork()** 시스템 콜이 새로운 프로세스를 생성

  - 부모를 그대로 복사(OS data except PID + binary)
  - 주소 공간 할당

- for 다음에 이어지는 **exec()** 시스템 콜을 통해 새로운 프로그램을 메모리에 올림

## 프로세스 종류

### 프로세스가 마지막 명령을 수행한 후 운영체제에게 이를 알려줌(exit)

- 자식이 부모에게 output data를 보냄(via wait).

- 프로세스의 각종 자원들이 운영체제에게 반납됨.

### 부모 프로세스가 자식의 수행을 종료시킴(abort)

- 자식이 할당 자원의 한계치를 넘어섬

- 자식에게 할당된 태스크가 더 이상 필요하지 않음

- 부모가 종료(exit)하는 경우

  - 운영체제는 부모 프로세스가 종료하는 경우 자식이 더 이상 수행되도록 두지 않는다.

  - 단계적인 종료

## fork() 시스템 콜

- fork() 시점의 코드부터 자식 프로세스가 따로 생성되어 실행됨

  - 부모와 자식은 서로 같은 코드를 가지지만 다른 프로세스로서 실행됨

  - pid > 0 -> parent process

  - pid = 0 -> child process

- fork()의 return value의 값 차이로 서로 다른 코드를 수행하게 짠다.

```c
int main()
{
    int pid;
    pid = fork();
    if(pid == 0) // this is child
        print("Hello, I am child!\n")
    else if(pid > 0) // this is parent
        print("Hello, I am parent!\n")
}
```

## exec() 시스템 콜

```c
int main()
    printf("\n Hello");
    execlp("/bin/date", "/bin/date", (char *)0);
    printf("\n Hello");
    // 새로운 프로그램으로 덮어씌우는 함수
    // 경로 포함 프로그램 이름, 프로그램에 전달할 argument, 0 포인터 로 구성
    // 프로그램을 덮어 씌우기 때문에 밑 코드들은 수행되지 않음
```
