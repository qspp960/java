## --------------------------------
## Exception (오류, 예외)
## --------------------------------

## 예외 / 오류
-- 프로그램 수행중 발생되는 문제(오류)
-- 자바는 예외도 객체로 처리
 		
## 예외에 대한 계층적 클래스 구조
	- java.lang.Trowable  
		=> Exception / Error	
			==> RuntimeException / IOException / SQLException
			
 1) Exception 계열 예외 클래스
			==> S/W 예외, 개발자가 예외발생 처리 가능
			==> 배열요소 범위 벗어나서 접근시, 0으로 나눔, 파일없음 등
			
 2) Error 계열 예외 클래스
			==> H/W 오류, 개발자가 예외발생 처리 불가능
			==> power off, cpu fail 등


## Exeption API : 
	0) 메서드
			-- public String getMessage() {} : 예외메세지를 문자열로 반환
			-- public void printStackTrace() {} : 예외발생 추적정보를 콘솔창 출력
			
	1) RuntimeException : 
			-- UnChecked Exception
			-- 자바 컴파일러가 예외처리 체크하지 않는 예외클래스
			-- NullPointerException
			-- ArrayIndexOutOfBoundsException
	
	2) IOException :
			-- Checked Exception 
			-- 자바 컴파일러가 예외처리 체크하는 예외클래스
			-- FileNotFoundException
			-- EOFException
			
	3) SQLException	
			-- Checked Exception
			-- DB 사용과 관련된 모든 예외를 발생


## 예외처리 방법 : 
-- 개발자가 명시적처리(try~catch~finally), 호출측에 예외처리 전가(throws)

(1) 명시적 예외처리 형식 : 
	-- 개발자가 메서드, 생성자 내부코드 구현부에서 명시적 예외처리 방법
		
	try {
		// 예외 발생 가능한 수행문
	} catch(서브예외클래스이름1 참조변수명) {
		// 서브예외클래스이름1에 대한 예외 처리 수행문
	} catch(서브예외클래스이름2 참조변수명) {
		// 서브예외클래스이름2에 대한 예외 처리 수행문
	} catch(슈퍼예외클래스이름 참조변수명) {
		// 슈퍼예외클래스이름에 대한 예외 처리 수행문
	} finally {
		// 정상수행 및 예외발생시에 반드시 수행되는 수행문
	}
		
(2) 호출측에 예외처리 전가 형식:
		-- 메서드 또는 생성자 선언시에 발생 가능 예외를 선언해서
	  -- 메서드 또는 생성자 호출 사용측에게 예외처리를 전가시키는 방법

	  -- 메서드 선언 형식:
	  modifier 반환타입 메서드이름() throws 예외클래스이름1, 예외클래스이름x {
		  if(예외발생조건) {
			throw new 예외클래스이름(parameters)
		  }		  
	  }
	  
	  -- 생성자 선언 형식:
	  modifier 생성자이름() throws 예외클래스이름1, 예외클래스이름x {}


3) 예외를 발생시키는 방법
 		1) 예외상황이 발생될때 JVM이 발생시킴
 		2) 개발자가 명시적으로 예외 발생 시킴
 				-- 테스트 목적 : 예외처리가 잘되나 확인
 				-- 사용자가 예외클래스를 정의해서 사용한 예외에 대해서 필요시 예외발생

4) 사용자가 예외를 발생시키는 방법
	throw new 예외클래스이름();
	throw new 예외클래스이름([args]);


5) 사용자 예외클래스 작성 방법 (규칙)
	(1) extends Exception
	(2) 생성자에서 부모의 생성자를 지정 : super("예외메세지문자열");
	(3) 필요시 멤버변수, 메서드, 생성자 중복정의 가능
	(4) 사용자 정의 예외는 컴파일러가 컴파일시점에서 예외처리 여부 검증 : 
		 - 예외처리 수행문 작성 : try ~ catch ~ finally 또는 throws 사용자정의예외클래스 
	(5) 개발자가 예외상황시에 명시적으로 예외 발생시킴:
		- throw new 사용자예외클래스이름();
		- throw new 사용자예외클래스이름([args-data]);


## 다중 예외처리시 주의 사항
	-- sub 예외클래스에 대한 catch 앞에서 처리 
			==> super 예외클래스에 대한 처리는 뒤에서 처리
	-- catch 하지 않은 예외에 대해서는 예외처리를 하지 않음것임
	-- 따라서 맨마지막에 catch(Exception e) {} 처리하게 되면
	   기타 등등 모든 예외에 대한 처리를 도맡아서 처리하게 됨
	   즉, 미처 처리하지 못한 예외에 대해서도 처리하는것이 되므로
	   프로그램이 강제종료되는것을 방지할 수 있음.
	   
