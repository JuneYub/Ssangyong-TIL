## 스태틱 변수
static 변수는 동일한 클래스로 생성되어진 서로 다른 instance(객체)들끼리 공유하는 변수이다.
static 변수를 class 변수라고도 부른다.

instacne(인스턴스)변수와 static 변수를 합쳐서 부를 때 member(구성원)변수라고 부른다.

instance 변수와 static 변수는 초기화를 하지 않더라도 자동적으로 초기화가 되어진다. 정수형인 데이터타입(byte,  short, int, long)은 자동적으로 0으로 초기화가 되고, 실수형인 데이터타입(float, double)은 자동적으로 0.0으로 초기화가 되고, 문자형인 데이터타입(char)은 자동적으로 ' '으로 초기화가 되고, String 을 포함한 클래스 타입은 자동적으로 null로 초기화가 된다.

사용방법
클래스명.static변수명 = 값;

클래스의 인스턴스(객체)에 값을 선언하는 것이 아닌
클래스의 속성 자체에 바로 값을 주는 것을 의미한다.


---------------------------------

## 지역변수
어떤 메소드 안에서 선언되어진 변수를 지역변수(local varialbe)라고 한다.

지역변수는 {} 내에서만 사용되어지기 때문에 {} 을 벗어나는 순간 자동적으로 메모리(RAM)에서 삭제가 되어진다.

지역변수는 반드시 초기화(어떤 변수에 처음부터 값을 부여해주는 것)을 해주어야 한다.!!

--------------------------------

프로그램이 끝나면 인스턴스에 할당되었던 공간을 비우는 것과
Garbage Collector(쓰레기 수집)을 하는 작업을 기술할 필요가 없다.

왜냐하면 프로그램이 종료되는 순간 이런 작업이 자동적으로 되기 때문이다.

------------------------------
## static 메소드
클래스내에 static 메소드가 있다면
다른 클래스에서 타 클래스의 static 메소드를 호출하고 싶을 때 타 클래스의 인스턴스를 만들어서 호출할 필요가 없다.

그냥 타 클래스.인스턴스메소드(); 하면 바로 호출할 수 있다.

------------------------------

## 자료형

자료형의 종류

원시형 타입(Primitive Type)

      1.1  정수형(byte, short, int, long)
       -- 자바에서 정수형의 기본타입은 int 이다.
        -- 그러므로 정수형의 값이 -2,147,483,648 ~ 2,147,483,647 범위를 벗어난 것이라면 반드시 숫자뒤에 소문자 l 또는 대문자  L 을 붙여야 한다.  
               
         byte (1byte == 8bit)  : -2^7(-2의 7승)  ~ 2^7-1(2의 7승 - 1)  ==> -128 ~ 127 
         short(2byte == 16bit) : -2^15 ~ 2^15-1 ==> -32,768 ~ 32,767
         int  (4byte == 32bit) : -2^31 ~ 2^31-1 ==> -2,147,483,648 ~ 2,147,483,647  
         long (8byte == 64bit) : -2^63 ~ 2^63-1 ==> -9,223,372,036,854,775,808 ~  9,223,372,036,854,775,807         
               
      
      1.2 실수형(float, double) 
          float(4byte)  : 단정밀도   소수점이하 7자리까지 표현됨.   135.3246235
         double(8byte) : 배정밀도   소수점이하 15~16자리까지 표현됨. 135.3246234502345642
       -- 자바에서 실수형의 기본타입은 double 이다. 
         그러므로 실수값을 float 형태로 나타내기 위해서는 실수뒤에 반드시 소문자 f 또는 대문자 F를 붙여야 한다. 
               
           
      1.3 문자형(char)
         char : 자바는 유니코드 체계를 사용하므로
                문자형 타입인 char 는 2byte 이며, 범위는 0 ~ 65535 이다.
                그래서 char 타입에는 문자 1개 또는 숫자(0~65535)도 올 수 있다.              
                                  
              UNICODE 표 참조 
              http://www.tamasoft.co.jp/en/general-info/unicode.html                     
           
꼭 기억합시다
           int(4byte) 아래의 크기인  byte(1byte), short(2byte), char(2byte) 타입이 사칙연산(+ - * /)을 만나면 자동적으로 int 타입으로 자동 형변환이 발생된다.
           
           'A' => 65     'a' => 97
           'B' => 66     'b' => 98
           'C' => 67     'c' => 99
           
           '대문자' + 32 => 소문자에 해당하는 숫자
           '소문자' - 32 => 대문자에 해당하는 숫자
           
           '0' => 48
           '1' => 49
           '2' => 50
           '9' => 57
           ' ' => 32
           
           
      1.4 참(true) 또는 거짓(false)을 담아주는 boolean 타입 
      -- 크기가 1byte 이다.
           
              
      2. 참조형 타입(Reference Type)
         --> 클래스 객체(==object ==instance) 타입   
         --> 메모리상에 저장되어진 객체의 메모리 주소를 참조하는 것이다.
         --> 참조형 타입(Reference Type) 메모리상에 크기는 4byte 를 차지한다.  
         ++ 속성, property, attribute, field ++
   
  
----------------------------------------

## 변수의 명명규칙 
1. 변수명의 길이에는 제한이 없다.
2. 대,소문자 구분이 있다.
3. 첫글자는 숫자는 안된다.
4. 특수문자는 '_' 와 '$' 만 사용이 가능하다. 
5. 예약어(예 package, import, public, class, String, int, float ...)는 변수명으로 사용불가하다.
6. 필수사항은 아니지만 변수명명규칙의 관례인데 카멜표기법과 스네이크표기법을 따른다.      