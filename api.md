## Class Node Type (클래스 종류)
-- Concrete Class
	>> 개발자가 자유롭게 필요시에 직접 객체 생성가능한 클래스
	>> 다형성을 반영한 부모타입의 변수 사용 가능
	>> 구성요소 : 멤버변수, 생성자, 메서드
	>> 부모 선언형식 : public class 부모클래스명 {}
	>> 현실세계어떤부모님?? : 재산만 상속해주시는 매우 감사한 부모님
	
	>> 자식클래스(상속) : 선택
	
	>> 자식클래스 선언형식 :
		public class 자식클래스명 extends 부모클래스명 {}
	
-- Abstract Class
	>> 미완성 클래스(추상클래스), 미완성 메서드(추상메서드)
	>> 직접 객체 생성불가 클래스 
	>> 다형성을 반영한 부모타입의 변수 사용 가능
	>> 추상메서드 존재시에는 반드시 추상클래스
	>> 추상메서드 없어도 상속을 강제하기위해서 추상클래스
	>> 구성요소 : 멤버변수, 생성자, 메서드 + [추상메서드]
	>> 부모 선언형식 : public abstract class 부모추상클래스명 {
					 public abstract 반환타입 추상메서드명(args);
				   }
	>> 현실세계어떤부모님?? : 재산 + 채무도 함께 상속해주시는 감사한 부모님				   

	>> 자식클래스(상속) : 필수

	>> 자식클래스 선언형식 :
		public class 자식클래스명 extends 부모추상클래스명 {}
	
-- Interface
	>> 다중 구현 (표준화)
	>> 다형성을 반영한 부모타입의 변수 사용 가능
	>> 구성요소 : 추상메서드, 상수로만 구성된 클래스 형태
	>> 부모 선언형식 : public interface 부모인터페이스명 {
					 public 타입 상수명 = 상수값;
					 public 반환타입 추상메서드명(args);
				   }
	>> 인터페이스에 선언되어 있는 메서드는 자동으로 public abstract 표기함(추상메서드)
	>> 인퍼페이스에 선언되어 있는 멤버변수는 자동으로 public static final 표기함(상수)
	>> 현실세계어떤부모님?? : 채무만 상속해주시는 그럼에도 불구하고 감사한 다중의 부모님
	
	>> 자식클래스(상속) : 필수
	
	>> 자식인터페이스(상속)
		public interface 자식인터페이스명 extends 부모인터페이스명 {}
		
	>> 자식클래스(구현)
		public class 자식클래스명 implements 부모인터페이스명1, 부모인터페이스명x {}
		
## 상속
-- Generalization(일반화)
	>> 공통 속성, 기능 일반화(표준화)
-- 단일상속	
-- 계층구조(tree 구조)

## Generic 
-- jdk1.5 추가
-- API 문서 : java.lang.Object
	<E> : 특정 Element Object 지정
	<K> : Key 해당하는 Object 지정
	<V> : Value 해당하는 Object 지정
	<T> : Type 해당하는 Object 지정
	
## usage modifier
-- static 멤버 : 클래스이름.static멤버변수명, 클래스이름.static멤버메서드명()
-- abstract
-- final	

## class node type : concrete class, abstract class, interface
## constructor : 접근가능, 중복정의

## API Documentation 만들기	
-- 회원관리 소스코드를 api문서 주석과 코드를 깔끔하게 정리진행해주세요
-- jdk\bin> 
	Usage: javadoc [options] [packagenames] [sourcefiles] [@files]	

-- eclipse> 컴파일 완성 >> 테스트 완료 >> API 문서 작성(개발 종료시에 문서작업 진행)
	>> 프로젝트선택 >> export >> Java >> javadoc
	
	>> 한글인코딩설정 : javadoc options => -encoding utf-8
	
-- api 문서주석 폴더 :
	>> project\docs\api\public> 공개용 api 문서
	>> project\docs\api\private> 내부용 api 문서
	
	
## 주요 API 활용
-- java.lang.Object	
	>> equals(Object) : boolean / hashCode() : int
	>> toString() : String

-- 문자열
	>> 문자열 비교시에는 equals() 메서드 사용해야함 
	
	>> java.lang.String : 
		=> 불변 문자열
		=> String name1 = "홍길동";
		=> String name2 = new String("홍길동");
	
	>> java.lang.StringBuffer : jdk1.0
	>> java.lang.StringBuilder : jdk1.5
		=> 가변 문자열
		StringBuilder name2 = new StringBuilder("홍길동");

-- 문자열 토큰링
	>> 구분자를 통해서 글짜를 분리(짤르기)
	>> csv : 컴마 구분자를 문자 분리 활용
	
	>> java.lang.String#split():String[]
	>> java.util.StringTokenizer(String, "+-*/% ,")
	
-- Wrapper
	>> 기본형 <-> 객체형 변환
	>> byte		-> Byte
	>> short	-> Short
	>> int		-> Integer
	>> long		-> Long
	>> float	-> Float
	>> double	-> Double
	>> boolean	-> Boolean
	>> char		-> Character
	
	>> "1234" => 1234
	>> Integer.parseInt("123");
	
	>> Integer intObj = new Integer("123");
	>> Integer intObj = new Integer(123);
	>> int data = intObj.intValue();

-- 날짜, 형식
	>> 가입일 : 가입당시 현재날짜(기본형식 : 년도4자리-월2자리-일2자리)
	>> java.util.Date : 현재날짜, 현재시간
	>> Calendar, GregorianCalendar
	>> java.text.DateFormat >> java.text.SimpleDateFormat
	>> java.util.Locale
	
	>> 날짜형식 => 문자열 변환 (com.work.util.Utility 유틸리티 클래스 분리설계)
	>> 시간형식 => 문자열 변환
	>> 년도 : yyyy
	>> 월 : MM
	>> 일 : dd
	>> 시간 : hh / HH / KK
	>> 분 : mm
	>> 초 : ss
	>> 오전/오후 : a
	
-- 숫자, 형식
	>> 마일리지 : 123456789 => 123,456,789
	>> 화폐 : 통화기호123,456,789


## Array (배열)
-- 자료 저장구조
-- 다차원
-- 기본형, 객체형 모두 가능, 상속전제 부모타입(다형성)
-- 고정 크기(확장 불가) : static collection
-- crud 기능 제공하지 않음
-- 배열명.length : 배열 크기 저장변수

## Collection API 활용
-- 자료 저장구조
-- 가변 크기 (자동 확장) : dynamic collection
-- 객체형 (Wrapper API 기본형, 자동 형변환 : int => Integer)
-- crud 포함한 다양한 메서드 제공

-- java.util.Collection : interface

-- java.util.List interface : 순서 존재, 중복 허용
	=> ArrayList **, LinkedLit, Vector 등

-- java.util.Set interface : 순서 없음, 중복 불가 
	=> HashSet **, TreeSet, SortedSet 등
	
-- java.util.Map interface  : 
	=> Key : Value
	=> Key : unique(중복 불가)
	=> HashMap **, Hashtable 등

## List CRUD 메서드 : 순서 존재, 중복 허용
-- equals() 메서드 재정의 여부에 따라 같은 객체여부 판단
-- 반환타입 E(Object) : instanceof, type casting 
-- C
	=> boolean	add(E e)
	=> void	add(int index, E element)
-- R
	=> E	get(int index)
-- U
	=> E	set(int index, E element)
-- D
	=> E	remove(int index)
	=> boolean	remove(Object o)
	
-- 저장크기
	=> int	size()

## Set
-- C : boolean	add(E e)
-- R : ??
	=> boolean	contains(Object o)

-- U : ??
-- D : 
	=> boolean remove(Object o)
	=> void	clear()

-- 저장크기
	=> int	size()

-- Iterator 반환타입 메서드??
	=> Iterator<E> iterator()
	=> Iterator interface

## Map >> HashMap
-- C
	=> V put(K key, V value) : key가 존재하지 않으면 추가
	=> Key data type : Object, String
	
-- R
	=> V	get(Object key)
-- U
	=> V put(K key, V value) : key가 존재하면 변경
	
	=> boolean	replace(K key, V oldValue, V newValue)
	=> V	replace(K key, V value)
-- D
	=> V	remove(Object key)
-- 저장크기
	=> int	size()

## Iterator
-- boolean	hasNext()
-- E	next()
-- boolean	remove(Object o)


## 중복정의 : 매개변수
doA("a", "b", "c");
doA("a", "b", "c", "d","e");
doA("a", "b");

## 회원가입, 등록 : 필수 속성 + 선택 속성

## 전체 : 변경
-- 기존 정보 (아이디 변경불가 : 읽기전용)
-- 나머지 : 필요시 변경 입력
-- 휴대폰, 이메일
-- 아규먼트 : 회원객체(아이디) => 저장위치 => set(저장위치인덱스, 아규먼트전달받은객체)
-- 회원 속성중에서 사용자가 임의로 변경해서는 안되는 속성?? : 아이디, 등급, 가입일, 마일리지, 담당자

## 부분 변경
-- 보안, 인증
-- 비밀번호 변경 
-- 아규먼트 : 아이디, 비밀번호, 변경할비밀번호 => 아이디 존재하는 저장위치 => 저장위치객체의 비밀번호 같은비교해 => 변경암호 변경처리

## 회원관리 기능 : 딱 3개만 기능 추가
-- 로그인
-- 아이디중복조회
-- 아이디찾기
-- 등급별 전체회원조회

## Generic

## Set

## Map

## Iterator

## ListIterator

## Collection 
-- jdk1.4
-- Object : 모든 객체 저장 가능한 자료 저장구조(Collection)
-- 다형성
-- 조회 : Object
	=> 부모타입은 자식객체 참조(referenc) 가능
	=> 타입 부모타입이므로 자식의 멤버는 접근 불가
	=> 실제 메모리에 생성한 자식객체의 멤버 접근
	=> instanceof 여부 체킹
	=> 실제 메모리에 생성한 자식객체 타입으로 형변환(type casting)
	
-- 예제 :
ArrayList list = new ArrayList();

list.add("hello"); 		// ok
list.add(1234); 		// ok
list.add(new Date()); 	// ok
list.add(new GeneralMember()); // ok
list.add(new SpecialMember()); // ok

Object obj = list.get(index);
if (obj instanceof 클래스이름) {
	클래스이름 참조변수명 = (클래스이름)obj;
}
	
## Generic
-- jdk1.5
-- 지정한 객체(Element) 타입의 전용 Collection

-- 예제 :
ArrayList<Member> list = new ArrayList<Member>();

list.add("hello"); 		// error
list.add(1234); 		// error
list.add(new Date()); 	// error

list.add(new Member()); // ok
list.add(new Member()); // ok

Member dto = list.get(index);
dto.getMemberId();
dto.getMileage();


## 회원관리 서비스 추가 기능 
	/*
	 * 로그인
	 * 	-- 처리절차
	 * 	-- 메서드명
	 * 	-- 매개변수
	 * 	-- 반환타입 ??
	 * 	1. 회원전용서비스 : boolean
	 *  2. 회원등급별 차등 서비스 : 로그인성공 - 해당회원의 등급(String), 로그인실패 - null (아이디 미존재, 비밀번호 불일치)
	 *  3. 로그인시에 자동 등업처리 : 
	 *  	=> 반환타입?? 로그인성공한 회원의 등급, 일반회원이 우수회원등업시 결과메세지
	 *  	=> 단일값 String, Domain 객체 Member xxx, Collection(List, Set, Map-key:value)
	 *  	3.1 : 로그인 성공??
	 *  	3.2 : 등급이 일반회원??
	 *  	3.3 : 일반회원이면 마일리지 변경(로그인 마일리지 추가)
	 *  	3.4 : 일반회원이면 마일리지가 현재 100,000이상이니??
	 *  	3.5 : 일반회원의 현재 마일리지가 100,000이상이면 
	 *  			=> 우수회원 등업처리를 위한 메서드 dispatch(위임)
	 *  			=> 우수회원등업요청(로그인성공한일반회원아이디) 
	 *  	3.6 : 일반회원이 우수회원으로 등업처리 결과를 받아서 : 담당자 결과 받아서
	 *  	3.7 : 우수회원으로 등업된 회원에게 "우수회원 등업처리 축하... 전용담당자 정보 "000" 로그인성공 응답
	 *  			=> 우수회원 등업의 결과를 출력 메세지 처리
	 *  			=> 응답결과로 반환
	 *  	4.0 : 로그인성공은 했으나 일반회원이 아니라면
	 *  	4.1 : 로그인 성공처리 응답
	 */
	
	/*
	 * 마일리지 변경 
	 * -- 마일리지 정책 ??
	 * 	1. 로그인시마다 일반회원인경우에는 마일리지 500 추가
	 */
	
	/*
	 * 우수회원 등업처리
	 * 	-- 처리절차(방법)
	 * 	1. 일반회원이 본인의 마일리지정보 조회하고 => 관리자에게(시스템) 등업요청
	 * 	2. 자동등업 : 
	 * 		=> 100,000점 넘으면 자동으로 등업  => 마일리지 변경처리 메서드에서 수행로직
	 *		=> 로그인 성공시 자동으로 확인해서 등업
	 *  3. 관리자 회원정보 조회해서 등업처리
	 *  
	 *  -- 처리절차
	 *  1. 아이디 매개변수 전달 => 일반회원?? 마일리지 100,000??
	 *  2. 등급 : 우수회원 변경
	 *  3. 담당자 : 배정
	 *  4. 마일리지 : 0 변경
	 *  5. 배정된 담당자 이름 반환
	 *  
	 * 	-- 메서드명
	 * 	-- 매개변수 : 회원아이디
	 * 	-- 반환타입 : 담당자
	 * 
	 * 	-- 담당자 고정지정
	 * 	-- 담당자 랜덤지정
	 */
	
	/*
	 * 아이디찾기 
	 * 	-- 처리절차
	 * 	-- 메서드명
	 * 	-- 매개변수
	 * 	-- 반환타입
	 */
	
	/*
	 * 비밀번호찾기 : 
	 * 1. 기존비밀번호 반환 : 현재 보안이슈...진행하는 사이트없어요..
	 * 2. 임시암호발급 변경후 반환 : 휴대폰 문자, 이메일 발송, 응답화면 메세지
	 * 3. 암호변경위한 메뉴 제공 :
	 * 	-- 처리절차
	 * 	-- 메서드명
	 * 	-- 매개변수
	 * 	-- 반환타입
	 */
