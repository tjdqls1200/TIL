## String 클래스 (java.lang 패키지 소속)

문자 배열, 문자 수를 나타내는 필드 등을 갖고 있는 클래스

많은 생성자와 메서드를 제공, 아래는 주로 쓰이는 메소드.

char charAt(int i)

- 인덱스가 i 인 곳의 문자를 가져온다.

int length()

- 문자열의 수를 가져온다.

boolean equals(String s)

- 문자열 s 와 같은가를 확인한다.



## 배열 개념 보충

배열의 길이는 0이어도 된다. (empty array)

배열 요소의 접근은 모두 런타임(실행 시)에 검사된다.

배혈 초기화는 마지막 요소에 대한 초기화 뒤에 추가로 쉼표를 넣을 수 있다. 

다차원 배열의 복제 .clone 은 각 행의 첫번째 열만 복제된다.  



## ArrayList

List 인터페이스를 상속받은 클래스로 크기가 가변적으로 변하는 선형리스트이다.

일반적으로 배열과 같은 순차리스트이며 인덱스로 내부 객체를 관리하지만 ArrayList 는 배열과 달리 객체를 추가하면 자동으로 저장 용량이 늘어난다.

'''

ArrayList<type> name = new ArrayList<type>();

name.add(index, value);

'''

index를 생략하면 자동으로 맨 뒤에 데이터가 추가되며 index 중간에 값을 추가하면 뒤에 있는 인덱스들은 뒤로 밀려난다.

remeve(index) - 해당 index 값 제거, 뒤에 있는 index들은 한 칸씩 당겨진다.

clear() - ArrayList의 모든 값을 제거한다.

size() - ArrayList 의 크기를 리턴.

contains(value) - 해당 value가 있으면 true, 없으면 false가 리턴.

indexOf(value) - 해당 value 값이 있는 index를 리턴.



### int 와 Integer 의 차이.

int (Primitive 자료형)

- '자료형'을 의미한다. (int, long, double == 하나의 primitive)
- 산술 연산이 가능하다.
- null 로 초기화가 불가능하다.



Integer (Wrapper 클래스-객체)

- Wrapper 클래스이다. 
  - Java 는 데이터를 기본형 타입(primitive) 와 객체 참조(클래스) 같은 두 가지의 타입으로 관리한다.
  - 기본형 타입을 객체로 사용하는 경우 Wrapper 클래스를 사용하여 나타낸다.
- Unboxing 을 하지 않으면 산술 연산이 불가능하지만, null 값은 처리할 수 있다.
  - 기본형 타입(primitive)을 객체로 사용하는 경우를 Boxing 한다고 한다. (반대는 Unboxing)
- 직접적인 산술연산은 불가능하지만 null 값 처리가 용이해서 SQL 과 연동할 경우 처리가 수월하다.



## 확장 for 문	

for (int i : array) [ 자료형 변수 : 배열]

기본 for문 외에 확장 for 문을 이용하여 간단하게 배열을 스캔할 수 있다. (배열의 길이를 몰라도 된다.) 

배열 array 의 안에 있는( : array)  / 요소(int i)를 배열의 처음부터 끝까지 하나씩 스캔한다.



## 클래스

여러 형의 요소를 조합하여 만든 자료구조를 클래스라 한다.

클래스 본체에서 선언 가능

		- 멤버(필드/ 메서드/ 중첩 클래스/ 중첩 인터페이스)
		- 클래스 초기화 / 인스턴스 초기화
		- 생성자
필드/ 메서드/ 생성자를 선언할 때 public/ protected/ private 지정 가능

메서드/ 생성자는 다중으로 정의(오버로드) 가능

final 로 선언한 필드는 한 번만 값을 대입 가능



### 파생 클래스

​	class B extends A (클래스 A 를 상위 클래스로 하는 서브 클래스 C)

​	extends 가 없는 클래스의 경우 상위 클래스는 Object 클래스

​	Object 클래스 : 모든 클래스의 상위 클래스 (java.lang 패키지에 소속)



### 인터페이스 

​	class X implements Y (인터페이스 Y 를 구현하는 클래스 X)



### 추상 클래스

​	클래스 접근 제한자 abstracts 를 붙여 추상 메서드를 가질 수 있는 추상 클래스 선언.

​	추상 메서드란 실체가 정의되지 않은 메서드로 실체는 서브 클래스에서 정의한다.

​	불완전한 클래스이므로 인스턴스를 만들 수 없다.



## 중첩 클래스

​	

## 알고리즘 목차

1. 검색

2. 스택, 큐
3. 재귀 알고리즘
4. 정렬
5. 집합
6. 문자열 검색
7. 리스트
8. 트리
9. 해시