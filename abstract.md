
-- final
	>> 변수 : 멤버변수, 매개변수, 변경불가
	>> 메서드 : 재정의불가
	>> 클래스 : 상속불가, String, System
-- static : Math, System
	>> static 멤버변수(객체들 공유변수), static 멤버메서드, static block init
	>> jvm memory : class area, stack area, heap area
-- instancof
-- type casting
-- oop
-- encapsulation, public, private
-- inheritance, 
-- polymorphism
-- overriding
-- java.lang.Object
-- equals() / hashCode()
-- toString()

## Usage Modifiers
-- static
-- final
-- abstract

## abstract
-- 추상 메서드
	=> 메서드의 선언부만 존재
	=> public abstract 반환타입 메서드명(타입 매개변수명, 타입 매개변수명);
	
-- 추상 클래스 
	=> 직접 객체 생성 불가
	=> 상속 강제 : 추상 메서드가 없는 경우에도 상속을 강제하는 목적으로 선언
	=> 추상메서드가 존재하면 반드시 추상클래스 선언부
	
-- 미완성 
	=> 메서드 선언부만 존재(표준, 방법, 규칙 정해놓음)
	=> 추상메서드
	=> 추상메서드가 존재하는 클래스는 반드시 추상클래스(미완성 클래스) 선언

-- 완성되지 못했기때문에 객체생성 불가
-- 미완성 => 완성(재정의 구현)

## 재정의(overriding) 규칙
-- 전제조건 : 상속불가
-- 동일 : 반환타입 메서드명 매개변수(갯수, 타입, 순서)
-- 접근권한: 확대가능(축소불가)
-- 예외 : 축소가능 (확대불가)

## 회원관리시스템 클래스 다이어그램
-- Domain : 
	>> 상속, encapsulation
	>> Member , GeneralMember, SpecialMember, AdminMember
-- Model : Service
	>> 추상클래스 : 표준화, 강제
	>> MemberServiceAbstract : 표준화(미완성 강제)
	>> MemberService : 표준화(상속 재정의)

## 무조건 등록 문제 : 중복 => 해결 : 등록하기전에 등록된 회원의 아이디가 같은지(같은객체 equals())
-- 메서드 분리설계 : 
	>> 반환타입?? => 2개, 1개
	>> 1개의 메서드 반환타입 : ?? int 
	>> 존재 유무 : 존재하면 해당 위치 인덱스반환, 존재하지 않으면 ??? => 배열요소 시작번호 0이니까, 0보다 작은숫자 : -1 반환
	>> 존재 유무 + 저장위치(배열요소번호)
	
-- 메서드명 형식 :
	>> public int exist(아이디) {}
	>> public abstract int exist(아이디);

## 관리 : CRUD
-- C 등록
	=> 존재 유무 체크 : boolean
-- R 상세조회(???) : 아이디 [, 비밀번호]
	=> 존재 유무 + ??? 저장위치(배열요소번호)
-- U 변경
	=> 존재 유무 + 저장위치(배열요소번호)
-- D 삭제(??) : 아이디 [, 비밀번호]
	=> 존재 유무 + 저장위치(배열요소번호)

















