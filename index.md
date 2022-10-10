# 1. 시작

 To Study List
```
 1. java
 2. git (github 블로그 사용)
 3. docker(k8s)  
 4. sql 
```

하루 공부한 분량을 
gitblog에 기록하기, 개발해온 내용을 docker로 패키징하기 

```
import java.util.*;

public class Main {

  public static void main(String[] args) {
    List<String> inputList = Arrays.asList("Hello", "world");
    long res = inputList.stream()
        .flatMap(data -> Arrays.stream(data.split("")))
        .count();
    System.out.println(res);
  }

}
```