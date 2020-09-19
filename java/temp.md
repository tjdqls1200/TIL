



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