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

>CPU burst : 프로그램 실행 중 CPU 연산(계산 작업)이 연속적으로 실행되는 상황<br>
>I/O burst : 프로그램 실행 중 I/O 장치의 입출력이 이루어지는 상황

## CPU 스케줄러(CPU Scheduler)
- `CPU가 유휴 상태`가 될 때마다, 운영체제는 `Ready Queue에 있는 프로세스 중에서 하나를 선택해 실행`해야 하며, 선택은 `CPU 스케줄러(CPU Scheduler)`에 의해 수행된다.
- CPU 스케줄러는 실행 준비가 되어 있는 메모리 내의 프로세스 중에서 선택하여, 이들 중 하나에게 CPU를 할당한다.