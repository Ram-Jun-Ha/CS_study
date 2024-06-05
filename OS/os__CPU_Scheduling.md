# 📌 CPU scheduling 
## 기본 개념
- single-processor system에서는 한 순간에 오직 하나의 프로세스만 실행될 수 있다.
- 나머지 프로세스들은 CPU가 free 상태가 되어, 다시 스케줄 될 수 있을 때 까지 기다려야 한다.

- `Multi-programming의 목적`은 CPU 이용률을 최대화하기 위해 `항상 실행 중인 프로세스를 갖게 하는 것`
- 이 방식에서, 어느 한 순간에 다수의 프로세스들을 메모리 내에 유지한다.
- 이후에 어떤 프로세스가 대기해야 하는 경우, 운영체제는 `CPU를 해당 프로세스로부터 회수하여 다른 프로세스에 할당`한다.

>CPU 이용률을 최대화 하는 것은 다중 프로세서 운영체제 설계의 핵심

## CPU-입출력 버스트 사이클 (CPU-I/O Burst Cycle)

>프로세스 실행은 CPU 실행(CPU Execution)과 I/O 대기(I/O wait)의 사이클로 구성된다.

![alt text](img/os_sceduling_01.png)

- 프로세스의 실행은 CPU Burst로 시작되며 `CPU burst-I/O burst - CPU burst - ..... `순으로 순차적으로 burst가 발생한다.
- 마지막 CPU burst는 실행을 종료하기 위한 시스템 요청과 함께 끝난다.

