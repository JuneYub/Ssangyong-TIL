## 자바로 파일 복사하는 방법

-----------------------

### 활용 방법 -> 게시글에 파일 첨부할 때
(코딩 공부를 할 때, 내가 배우는 부분을 어떻게 활용할지 고민하면 좋다고 합니다)

</br>

*** 전체 코드 ***
```

public class FileCopty_test_9 {

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
		System.out.println("복사할 원본파일명을 입력하세요");
		String orgFilePath = sc.nextLine();
		System.out.println("붙여넣기 할 위치를 입력하세요");
		String outFilePath = sc.nextLine();
		
		
		byte dataArr[] = new byte[1024]; //  1kb = 1024 byte
		
		int inputLength = 0;

		
		try {
			
			FileInputStream fist = new FileInputStream(orgFilePath);
			FileOutputStream fost = new FileOutputStream(outFilePath);
			
			while( (inputLength = fist.read(dataArr, 0, dataArr.length) ) != -1) {
				
				fost.write(dataArr, 0, inputLength);
				
			}
			
			fost.flush();
			
		} catch(FileNotFoundException e) {
			
			e.printStackTrace();
			
		}  catch (IOException e) {
			
			e.printStackTrace();	
		}
		
	}

}

```

![](https://velog.velcdn.com/images/qkrwnsduq/post/54d9745e-ac42-44e7-a5d0-d82f4f9e272d/image.png)

dataArr 는 1kb 짜리 빨대입니다. 자 이제 이 빨대를 활용해보겠습니다.

FileInputStream 은 빨대를 꽂을 준비하는 것입니다.

FileOutputStream 은 input으로 가져온 내용을 다른 곳으로 빨대를 통해 흘려보내는 것입니다.

fist.read는 빨대를 통해 -1 이 아니라면 1kb의 내용을 흡입합니다.

이것을 fost.write 를 통해 지금 빨대에 있는 1kb의 내용을 파일 붙여놓기 하고싶은 공간으로 흘려보냅니다 ㅎㅎ

```
try {
			
			FileInputStream fist = new FileInputStream(orgFilePath);
			FileOutputStream fost = new FileOutputStream(outFilePath);
			
			while( (inputLength = fist.read(dataArr, 0, dataArr.length) ) != -1) {
				
				fost.write(dataArr, 0, inputLength);
				
			}
			
			fost.flush();
			
		}
```

flush() 는 버퍼를 비우는 기능으로 스트림에 에러가 발생하면 버퍼내에 데이터쪼가리가 남을 수도 있기에 비워야 한다고 합니다. 

close() 는 내부에 flush()가 있지만 직접 비워주는게 좋다고 합니다

-----------------------

