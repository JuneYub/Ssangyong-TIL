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