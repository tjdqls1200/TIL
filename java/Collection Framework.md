## Collection Framework (Iterator)

![cllection_framework](./image/cllection_framework.png)

- Collection 프레임워크란 데이터를 저장하는 클래스들을 표준화한 설계로 데이터를 저장하는구조에 따라 3가지 인터페이스로 생성된다. (Set, List, Map 은 어떤 데이터들의 집합체)
- Set 은 순서를 유지하지 않는 데이터의 집합으로 데이터의 중복을 허용하지 않는다.
- List는 순서를 유지하는 데이터의 집합으로 데이터의 중복이 허용된다.
- Map 은 Key 와 Value 로 이루어진 데이터의 집합으로 순서는 유지되지 않으며 Key 는 중복을 허락하지 않는다. 

### Iterator (java.util.Iterator)

- Iterator는 위의 Collection 프레임워크에서 저장되어 있는 요소들을 읽어오는 방법을 표준화한 것이다.
- ArrayList 를 탐색할 때 주로 사용되며 객체에 저장된 값을 하나씩 순회할 수 있다.
- Iterator iter = list.iterator() 
- Iterator 메소드에는 hasNext() -> next(), remove() 가 있다.
  - hasNext() : 읽어올 요소가 남아있는지 확인하는 메소드, 요소가 있으면 true, 없으면 false 리턴
  - next() : 다음 데이터를 반환한다.
  - remove() : next() 로 읽어온 요소를 삭제한다.