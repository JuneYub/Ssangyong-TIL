## 1. DecimalFormat

</br>

```

DecimalFormay df = new DecimalFormat("#,###");
String str_money = df.format(money);

```

문자열의 형식을 바꿔주는 클래스로 패턴에 따라 의미가 달라진다.
패턴 0의 경우 10진수로 표현하며 빈자리는 0으로 채운다.
패턴 #의 경우 10진수로 표현하며 빈자리는 채우지 않는다.

+, - 등을 사용해서 음수 양수를 표시할 수도 있다.

## 2. 멀티 스레드

```스레드```란 -> 실제로 작업을 수행하는 단위 </br>
```싱글 스레드``` - 프로세스가 하나의 스레드로 동작 </br>
```멀티 스레드``` - 프로세스가 동시에 두 개 이상의 스레드로 동작

### 멀티 스레드 클래스 구현 방법

1. Thread 클래스를 상속

```
    public class ThreadA extends Thread {
        public void run() { // 런 메소드 오버라이딩

            // 스레드 실행 블럭
            // 스레드 실행 블럭
        }
    }

    ThreadA ta = new ThreadA(); // Thread 객체 생성
    ta.start(); // 스레드 실행 -> 스레드 실행 블럭

```

2. Runnable 인터페이스를 구현

```
    public class ThreadA implements Runnable { // 인터페이스 구현
        public void run() { // 런 메소드 오버라이딩

        }
    }

    Runnable ra = new ThreadA(); // Runnable 참조 객체 생성
    Thread ta = new Thread(ra); // Thread 객체 생성
    ta.start();

```

이후에 run() 메소드를 오버라이딩 하여 run 메소드 내에 무한 반복문을 사용하여 프로그램을 작성한다. </br> run 메소드가 스레드로 작동하는 것이고 이를 시작하기 위해서는 start() 메소드를 호출하면 된다.


멀티 스레드를 제어하는 방법은 스레드의 우선순위를 제어함으로써 가능하다.</br>
기본 우선순위는 5이고 우선순위의 범위는 1 ~ 10 이다.

```데몬 스레드``` 
> 일반 스레드의 작업을 돕는 보조적인 스레드 </br>
>일반 스레드가 모두  종료되면 자동 종료된다.


```동기화```
>여러 개의 스레드가 하나의 자원을 사용할 때 필요</br>
하나의 스레드가 자원을 사용한 다음, 다른 스레드가 자원을 사용 </br>
하나의 스레드가 작업중인 것을 다른 스레드가 간섭하지 못하도록 함 


