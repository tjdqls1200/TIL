# 문자열 내 p 와 y 의 개수

## Programmers, Level 1

문자열 내 'p' 와 'y' 의 개수를 비교해서 같으면 true 다르면 false 를 리턴한다. (대소문자 구분 X)



## 1. 풀이 코드

```
import java.util.Arrays;

class Solution {
    boolean solution(String s) {
        int pNumber = 0;
        int yNumber = 0;
        char ch;

        for(int i = 0; i < s.length(); i++) {
            ch = s.charAt(i);
            if(ch == 'p' || ch == 'P') {pNumber++;}
            else if(ch == 'y' || ch == 'Y') {yNumber++;}
        }
        return (pNumber == yNumber) ? true : false;
    }
}
```



## 2. 참고 코드

```
class Solution {
    boolean solution(String s) {
        s = s.toUpperCase();

        return s.chars().filter( e -> 'P'== e).count() == s.chars().filter( e -> 'Y'== e).count();
    }
}
```

## 3. 문법

람다식 공부.