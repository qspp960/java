## 회원관리 시스템 예외상황 ??
-- null 오류??	
	=> NullPointerException 활용
	=> 필수항목 미입력시에 예외 : RequiredException 사용자 정의사용

-- 등록안될때??
	=> 아이디가 중복된 경우 : DuplicateException 사용자 정의사용
	=> ??? 필수항목 미입력시 
	
-- 조회가 안될때, 변경이 안될때, 탈퇴가 안될때
	=> 미등록상태(아이디가 존재하지않을때) : RecordNotFoundException 사용자 정의 사용
	=> 변경 : 필수항목 누락된경우
	=> 탈퇴 : 아이디, + 비밀번호 (데이터 일치하지않을때)
	
-- 회원등급 : G, S, A 아닌경우 발생?? : InValidDataException 사용자 정의 사용
-- 마일리지 : 0 ~ 100000
	=> 로그인시에 마일리지 부여(500 씩 부여)
	=> 로그인 사용자, 일반회원, 현재 99,800 => 로그인성공 99,800 + 500 = 100,300
	
## 공통 예외클래스 
-- CommonException 사용자 정의 사용

## 중복 예외클래스
-- DuplicateException
-- 아이디, 휴대폰, 이메일 등록

## 데이터 미존재
-- RecordNotFoundException

 
## 입력/출력
-- java.io package
1. input/output??
	-- 입력 스트림
	-- 출력 스트림	
	
2. device ?? => NodeStream	
	-- 표준입력(키보드) : 
		=> System.in
		=> static InputStream	in
		=> byte 읽기전용 스트림
		
	-- 표준출력(모니터) : 
		=> System.out
		=> static PrintStream	out

	-- 파일 : 
		=> String filename
		=> java.io.File
		
3. 데이터 단위
	-- byte(1byte => 8bit) : 
		=> 이미지, 음원, text(영문자, 숫자)
		=> XxxStream
		=> InputStream, OutputStream
		=> FileInputStream, FileOutputStream
		
	-- character(2byte => 16bit) : text(영문자, 숫자, 한글, 중국어...)
		=> XxxReader, XxxWriter
		=> FileReader, FileWriter
		
4. Filter Stream(Processing Stream) 추가 여부??		
	-- InputStreamReader() : byte => character 변환 기능
	-- BufferedReader()    : character => String (라인단위 읽기)
	
	-- PrintWriter : 라인단위 출력
	
## I/O 관련 예외
-- Exception
	>> IOException : checked exception (예외처리)
		>>> EOFException
		>>> FileNotFoundException
