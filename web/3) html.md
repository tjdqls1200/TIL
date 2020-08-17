# HTML

### 1. HTML이란?

- 브라우저에서 실행 가능한 가장 기본적인 파일
- Mark-up 언어로 Tag를 이용하여 구조적으로 표현



### 2. 구조

```html
<html>

​	<head>

		<meta charset=“utf-8”>

		<meta name=“viewport” content=“width=device

​	</head>

​	<body>

​	</body>

</html>

```

**1) html**

- 최상위 tag

**2) head (상세 설명)**

- 사용자에게 보여지는 ui적인 요소가 전혀 없다. 
- 검색 시 나오는 타이틀이나 제목, 아이콘 등이 정의되어 있다. CSS 파일을 연결하는 것도 head가 진행

**3) body (사용자에게 보여지는 영역)**

- 사용자에게 보여지는 영역



### 3. 특징

- html은 문법이 조금 틀려도 브라우저가 자동으로 수정 (validator 사이트에서 문법 체크 가능)
- 웹을 볼 때 자세한 구조로 나누어 볼 줄 알아야 하는 이유
  - CSS를 할 때 structure하게 작업이 가능
  - react 프레임워크를 사용할 때 작은 단위로 최대한 나누어 구현하는 것이 좋음

Tag -> Box, Item 두 종류로 분류

- **Box :**  아이템을 잘 정리할 수 있도록 도와주는 보이지 않는 박스
  - header
  - nav
  - aside 
  - main
  - footer
  - section
  - article
  - div
  - span
  - form

- **Item :** 사용자에게 보여지는 아이템
  - a
  - button
  - input
  - label
  - img
  - video
  - audio
  - map
  - canvas
  - table 

command + option + i