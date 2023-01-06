## 1. Scanner
Scanner sc = new Scanner
생성자를 활용해서 scanner를 만든 후에는
sc.close()를 통해서 메모리를 정리해줘야 한다.

---------------------------------------------

## 2. try catch문

```
int progress = 0;
try {
    메소드1()

    progress = 1;
    메소드2()
}
catch(Numberformat e) {
    if(progress == 0)
    if(progress == 1)
}
```

try catch문을 통해서 메소드 개별적으로 오류를 출력하는 방법은
try문이 시작하기 전에 flag 값을 주고 개별 메소드 앞에서
flag마다 개별적인 오류문을 출력할 수 있도록 한다.

------------------------

## 3. 박싱 언박싱

     Boxing(박싱, 포장을 하는것) 이란 ?
      // ==> 기본자료형(boolean, byte, short, int, long, char, float, double)으로 되어진 변수를 객체타입인 
      Wrapper 클래스(Boolean, Byte, Short, Integer, Long, Character, Float, Double) 타입의 객체로 만들어주는 것을 말한다.
      
      
      // UnBoxing(언박싱, 포장을 푸는것) 이란?   
      // ==> Wrapper 클래스(Boolean, Byte, Short, Integer, Long, Character, Float, Double)로 되어져 있는 객체를 
      기본자료형(boolean, byte, short, int, long, char, float, double)으로 만들어주는 것을 말한다.