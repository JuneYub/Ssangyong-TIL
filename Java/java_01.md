
## 1. 패키지 선언 

패키지란 클래스가 저장되어진 디렉토리(폴더)경로라고 보면 된다.
package 패키지명; ===> 이때 패키지명은 반드시 소문자로 시작해야 한다.

예) package my.day01;

## 2. import 문

예) import 패키지명.클래스명;
    
   import java.lang.System;
   import java.lang.*;   \*의 뜻은 모든 것을 의미한다.
   
   기본적으로 import java.lang.*; 은 생략되어져 있다.
   
## 3. 클래스 선언문
 
 클래스명은 반드시 파일명과 동일해야 하며, 첫글자는 대문자로 시작해야 한다.
파일명의 확장자는 반드시 .java 이어야 한다.

    public class HelloExam
    {  // class body(클래스 본체) 는 { 로 시작해서 } 로 끝난다.

      public static void main(String[] args) { // 메인 메소드라고 부른다.
                                               // 메인 메소드가 자바 콘솔(키보드와 모니터로만 이루어진 것) 프로그래밍 실행의 시작과 끝을 나타내는 부분이다.
                                               
       		System.out.print("Hello World"); // System.out 은 모니터(화면)라고 보면 된다.
      	
            System.out.print("안녕하세요");
			
            
            // java.util.Date now  = new Date();
            Date now = new Date();
            System.out.print("현재 시각 : " + now);
      }

    }

--------------------------------