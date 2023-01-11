## 1. 자바 난수 생성
</br>


### 1-1 Math 클래스를 활용하는 법
</br>

java에서 임의의 수를 구하고 싶을 때 Math 클래스에서 random 함수를 활용하면 된다.


```
double randomfloat = Math.random(); // 0.0 ~ 1.0 사이의 난수 1개 발생

int randomInt = (int)(Math.random()*100); // 0 ~ 100 사이의 랜덤 숫자

```
Math.random에 원하는 끝 수를 곱해주면 된다.

</br>

### 1-2 Random 클래스를 활용하는 법

```

    Random rd = new Random();
    rd.setSeed(System.currentTimeMillis()); // 시드값 설정을 하지 않으면 난수지만 같은 결과가 나올 수 있다.


    // 1 ~ 3 까지 중 랜덤한 숫자 한개 만드는 방법
    
    int randomNum = rd.nextInt(3 - 1 + 1 ) + 1;
    // rd.nextInt(끝 수 - 첫 수 + 1) + 첫 수

  
```
nextInt(int i)가 0부터 i-1까지의 랜덤한 숫자를 리턴하다보니
1~3이라면 0~2가 리턴되기에 + 1을 해주는 것이다.

3 ~ 6이라면
rd.nextInt(6 - 3 + 1) + 3 으로 하면 된다.

-------------------------

</br>

## 2. equalsIgnoreCase()

</br>

String 클래스의 메소드로
대소문자와 상관없이 문자열이 같은지 비교해주는 메소드이다.

```
s1 = "abcd";
s2 = "ABCD";

s1.equalsIgnoreCase(s2);  // true

```


