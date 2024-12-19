[동시성 제어 방식에 대한 분석 및 보고서 작성]


1. 동시성 제어 메커니즘: ReentrantLock

ReentrantLock은 자바의 java.util.concurrent.locks 패키지에서 제공하는 명시적 락입니다. ReentrantLock은 여러 스레드가 동시에 공유 자원에 접근하려 할 때, 이를 동기화하는 방법으로 사용됩니다. 이 락은 임계 영역을 보호하고, 스레드가 자원에 접근할 수 있는 순서를 제어하여 동시성 문제를 해결합니다.
1.1 ReentrantLock 특징
-재진입 가능: 동일한 스레드가 이미 락을 획득한 상태에서 다시 락을 획득할 수 있습니다. 이를 재진입(lock re-entry)이라고 하며, 주로 자원 사용 중에 다른 자원을 잠금해야 할 때 유용합니다.
-명시적 제어: synchronized 키워드와 달리 ReentrantLock은 명시적으로 락을 획득하고 해제할 수 있어 락의 제어가 좀 더 세밀합니다.
-공정성 (Fairness): ReentrantLock은 공정성을 제공할 수 있습니다. 즉, 요청 순서대로 락을 부여하는 방식으로 공정하게 자원에 접근할 수 있습니다. 기본적으로는 비공정(non-fair) 락이지만, 생성자에서 true를 넘기면 공정한 락을 구현할 수 있습니다.
-중단 가능 (Interruptible): synchronized 키워드가 블로킹 상태에서 인터럽트가 불가능한 반면, ReentrantLock은 lockInterruptibly() 메서드를 통해 인터럽트가 가능하여 스레드가 종료되거나 다른 조건에서 쉽게 해제될 수 있습니다. 2.2 사용 방식 ReentrantLock을 사용하는 방식은 매우 간단하며, 아래와 같은 절차로 동작합니다:
-락 획득: lock.lock()을 호출하여 락을 획득합니다.
-임계 구역: 락을 획득한 후, 임계 구역에서 공유 자원을 안전하게 사용할 수 있습니다.
-락 해제: 작업을 마친 후 lock.unlock()을 호출하여 락을 해제합니다.

2. 동시성 제어 구현: 사례 분석
2.1 PointService 사용 사례 PointService 클래스는 포인트 충전 및 사용 기능을 제공하며, ReentrantLock을 사용하여 동시성 문제를 해결하고 있습니다. 예를 들어, usePoint 메서드는 특정 유저의 포인트를 사용하려 할 때 동시 요청이 발생할 수 있는 상황에서, ReentrantLock을 사용하여 포인트의 과도한 사용을 방지하고 있습니다.
2.2 동시 요청 시 문제 해결 여러 스레드가 동시에 usePoint 메서드를 호출하면, 포인트 차감 작업이 중복되거나, 잔액이 부족한 상황에서 과도한 포인트 사용을 시도할 수 있습니다. ReentrantLock을 사용함으로써, 한 스레드가 포인트를 사용하는 동안 다른 스레드들은 대기하게 되어, 포인트 잔액의 일관성을 유지할 수 있습니다.
2.3 경쟁 조건(Race Condition) 방지 경쟁 조건은 두 개 이상의 스레드가 동시에 동일한 자원을 수정하려고 할 때 발생합니다. 이 경우, ReentrantLock을 사용하면 한 스레드가 자원을 수정하는 동안 다른 스레드는 접근하지 못하도록 막을 수 있습니다. 이로써 데이터의 무결성과 일관성이 보장됩니다.

3. 교착 상태(Deadlock) 방지 전략
ReentrantLock을 사용할 때 교착 상태가 발생하지 않도록 하기 위한 전략은 다음과 같습니다:
-락 획득 순서 정하기: 여러 락을 사용할 때 항상 동일한 순서로 락을 획득하도록 하여, 서로 다른 순서로 락을 획득하는 스레드 간의 교착 상태를 방지합니다.
-타임아웃 설정: 락을 획득하는 데 시간이 너무 오래 걸리면 타임아웃을 설정하여 무한 대기를 방지할 수 있습니다.
-락 해제 보장: 락을 획득한 후 예외가 발생하더라도 finally 블록을 사용하여 반드시 락을 해제하도록 합니다.

