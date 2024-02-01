# 240201] 12930. 이상한 문자 만들기

[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/12930)

### 문제 설명
문자열 s는 한 개 이상의 단어로 구성되어 있습니다. 각 단어는 하나 이상의 공백문자로 구분되어 있습니다. 각 단어의 짝수번째 알파벳은 대문자로, 홀수번째 알파벳은 소문자로 바꾼 문자열을 리턴하는 함수, solution을 완성하세요.

**제한 사항**  
* 문자열 전체의 짝/홀수 인덱스가 아니라, 단어(공백을 기준)별로 짝/홀수 인덱스를 판단해야합니다.  
* 첫 번째 글자는 0번째 인덱스로 보아 짝수번째 알파벳으로 처리해야 합니다.

### 풀이
```java
class Solution {
    public String solution(String s) {
        String[] array = s.split(" ", -1);
        
        for(int i = 0; i < array.length; i++) {
            StringBuilder sb1 = new StringBuilder(array[i].toLowerCase());
            StringBuilder sb2 = new StringBuilder(array[i].toUpperCase());
            
            for(int j = 0; j < sb1.length(); j += 2) {
                    sb1.setCharAt(j, (sb2.charAt(j)));
            }
            
            array[i] = sb1.toString();
        }
        
        return String.join(" ", array);
    }
}
```

### 성능 요약
통과 (0.15ms, 74.1MB)

## 참고
Java - Map getOrDefault() Method - 찾는 키가 존재한다면 찾는 키의 값을 반환하고 없다면 기본 값을 반환한다.  
> getOrDefault(Object key, V defaultValue)

###  다른 풀이
```java
import java.util.*;

class Solution {
    public int[] solution(String s) {
        int[] answer = new int[s.length()];
        HashMap<Character,Integer> map = new HashMap<>();
        for(int i=0; i<s.length();i++){
            char ch = s.charAt(i);
            answer[i] = i-map.getOrDefault(ch,i+1);
            map.put(ch,i);
        }
        return answer;
    }
}
```
