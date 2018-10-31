# Stack, Queue
+ STACK
    + LIFO(Last In First Out)의 후입선출 구조
    + push();를 이용한 데이터 입력, pop();을 이용한 데이터 출력
    + 예) 시스템 스택 : 함수의 호출과 복귀 순서는 스택의 구조를 응용하여 관리
+ QUEUE
    + FIFO(First In First Out)의 선입선출 구조
    + enQueue();를 이용한 데이터 입력, deQueue();를 이용한 데이터 출력
    + 예) 우선순위가 같은 작업 예약(인쇄 대기열), 선입선출이 필요한 대기열(티켓 카운터)
    + **Linear Queue(선형큐)** 는 메모리 재사용이 불가능, 이러한 문제점을 보완하여 **Circular Queue(원형큐)** 가 나옴