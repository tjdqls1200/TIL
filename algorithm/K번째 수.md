# K번째 수 (Programmers, Level 1)

## 복사

### 1. copyOf(array, length)

- length 길이만큼 배열을 복사

### 2. copyOfRange(array, startIndex, endIndex)

- 배열의 start index 이상 ~ end index 미만까지 특정 범위를 복사한다.



## 정렬

java.util 라이브러리에는 Collections 라는 하위 라이브러리가 존재, 다양한 기능을 제공(정렬, 셔플 등)

### sort(array, startIndex, endIndex)

- 배열의 요소를 오름차순으로 정렬, index 없으면 전체 정렬.

### sort(array, reverseOrder())

- 배열의 요소를 내림차순으로 정렬.



## 코드

import java.util.Arrays;

class Solution {
    public int[] solution(int[] array, int[][] commands) {
        int[] answer = new int[commands.length];

        for(int i=0; i<commands.length; i++) {
            int[] extractOfArray = Arrays.copyOfRange(array, commands[i][0]-1, commands[i][1]);
            Arrays.sort(extractOfArray);
            answer[i] = extractOfArray[commands[i][2]-1];
        }
        return answer;
    }
}