## 1. 예외처리 클래스 만들기  
--------------------  

가게에서 손님한테 과자주문을 받는다고 할 때 </br>
가지고 있는 수량보다 주문 수량이 많으면 주문을 못받는 예외처리를 </br> 
예외처리 클래스를 구현하여 만들어보자 </br>

1. Product 클래스에는 order 메소드가 구현되어 있다.
try catch를 통해서 잔고보다 많은 주문량이 발생되면 JangolackException 이 발생되게 했다.  
</br>

```
	public void order(int jumunsu) throws JangolackException {
		
		if(jango < jumunsu) {
			
			throw new JangolackException(">> " + prodName +"은 잔고가 "
            + jango +"개 인데 주문량이 "+ jumunsu 
            +"개라서 잔고 부족으로 주문이 불가합니다.<<");
		} 

		else {
			jango -= jumunsu;
			System.out.println(prodName + "제품을" + jumunsu + "개 주문하셨습니다");
		}
	}
```

</br>

2. 예외처리 클래스인 JangolackException 클래스이다. </br>
이곳에서 기본생성자를 활용한 JangolackException 예외처리 방법과 </br>
오버로딩을 통해 파라미터가 있는 JangolackException 예외처리 방법이 있다. </br>
앞선 order 메소드에서는 String 파라미터를 넘겨주는 예외처리 방법이다.  

</br>

```
public class JangolackException extends Exception {
	
	static final long serialVersionUID = 1L;
	// 기본생성자
	
	public JangolackException() {
		super(">> 잔고량이 주문량보다 적으므로 주문이 불가합니다. <<");
	}
	
	
	// 파라미터가 있는 생성자
	public JangolackException(String errMsg) {
		super(errMsg);
	}
}

```

</br>

3. 출력결과 
JangolackException은 파라미터로 받은 아래 String 내용을 super(errMsg)를 통해 Exception으로 넘겨 출력한다.

</br>

```
throw new JangolackException(">> " + prodName +"은 잔고가 "
            + jango +"개 인데 주문량이 "+ jumunsu 
            +"개라서 잔고 부족으로 주문이 불가합니다.<<"); 
```

</br>

이처럼 ArraysIndexOutOfBoundsException , ArithmeticException , NuberFormatException 등의 기본 예외처리 말고도
자신만의 예외처리 클래스를 구현하여 활용할 수 있다.


-------------------------------

</br>

## 2. 람다문 만드는 법
--------------------  
***사용 목적***  </br>

자바에서 람다식의 사용 목적은 인터페이스에 정의된 메소드를 구현시  </br>
코딩양을 확 줄여서 간편하게 사용하는 것이 목적이다.

</br>

***1. 인터페이스를 만든다.*** </br>

***2. 함수명 위에 @FunctionalInterface 를 쓴다.***

```
@FunctionalInterface
public interface InterfaceExample {
	
	함수();
}

```

FunctionalInterface 가 어노테이션으로 추가되면 </br>
인터페이스에는 하나의 함수만 쓸 수 있다.

람다식은 익명함수를 생성하기 위한 식으로 함수 지향 언어에 가까운게 특징이다.

그래서 functional interface 어노테이션을 통해 메소드를 하나로만 제한하다 보니 인터페이스가 하나의 함수를 대표하게 된다. </br> 
따라서 간결하게 표현할 수 있게 되는 것이다. </br>

</br>
</br>

***3. 람다식 구현법***

```
InterfaceExample lambda = () -> { // 파라미터가 없으면 ()으로 표현

}

```

기억하자  
```
인터페이스이름 람다 = (파라미터) -> {

}
```

```
인터페이스이름 람다명 = (a, b) -> a+b; // 한줄로도 표현 가능

인터페이스이름 람다 = (a, b) -> {return a;}; // 하지만 리턴값이 있으면 괄호를 꼭 붙여줘야 한다.
```  



