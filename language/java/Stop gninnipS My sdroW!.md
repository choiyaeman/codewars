# Stop gninnipS My sdroW!

Instructions>

Write a function that takes in a string of one or more words, and returns the same string, but with all five or more letter words reversed (Just like the name of this Kata). Strings passed in will consist of only letters and spaces. Spaces will be included only when more than one word is present.

Examples: spinWords( "Hey fellow warriors" ) => returns "Hey wollef sroirraw" spinWords( "This is a test") => returns "This is a test" spinWords( "This is another test" )=> returns "This is rehtona test"

```java
public class SpinWords {

  public String spinWords(String sentence) {
    //TODO: Code stuff here
    StringBuilder sb = new StringBuilder();
    String[] splitSentence = sentence.split(" ");
    
    for(String word : splitSentence){
      if(word.length()>4){
        sb.append(new StringBuilder(word).reverse().toString() + " ");
      } else {
        sb.append(word + " ");
      }
    }
    return sb.toString().trim();
  }
}
```

```java
import org.junit.Test;
import static org.junit.Assert.assertEquals;

public class SpinWordsTest {
    @Test
    public void test() {
      assertEquals("emocleW", new SpinWords().spinWords("Welcome"));
      assertEquals("Hey wollef sroirraw", new SpinWords().spinWords("Hey fellow warriors"));
    }  
}
```

---

### **split 함수**

→입력 받은 정규표현식 또는 특정 문자를 기준으로 문자열을 나누어 배열(Array)에 저장하여 리턴

public String split(String regex)

public String split(String regex, int limit)

- regex: 문자열을 구분하기 위한 정규 표현
- limit: 분류할 문자열의 수. 분류할 수 있는 단어가 10개인데 limit가 5이면 5개만 구분하고 나머지는 통채로 출력한다.

### **Java에서 문자열 붙이기**

- 플러스(+)

    String a = "첫번째 강아지는 콩쥐입니다.";

    String b = "두번째 강아지는 팥쥐입니다.";

    System.out.println(a+b); 

    //결과값: 첫번째 강아지는 콩쥐입니다. 두번째 강아지는 팥쥐입니다.

- Concat

    String a = "첫번째 강아지는 콩쥐입니다.";

    String b = "두번째 강아지는 팥쥐입니다.";

    System.out.println(a.concat(b)); 

    //결과값: 첫번째 강아지는 콩쥐입니다. 두번째 강아지는 팥쥐입니다.

- Append

    StringBuilder sb = new StringBuilder("첫번째 강아지는 콩쥐입니다.");

    sb.append("두번째 강아지는 팥쥐입니다.");

    sb.append("세번째 강아지는 콩순이입니다.");

    //결과값: 첫번째 강아지는 콩쥐입니다. 두번째 강아지는 팥쥐입니다. 세번째 강아지는 콩순이입니다.

**append()메소드**

-인수로 전달된 값을 문자열로 변환한 후, 해당 문자열의 마지막에 추가. 즉, 이어 붙이는 것.

-이 메소드는 String클래스의 concat()메소드와 같은 결과지만, 내부적인 처리 속도가 훨씬 빠름.

-append()메소드를 사용하기 위해서는 StringBuffer클래스를 임포트해야 함.

### **Trim()**

문자열의 처음과 마지막의 공백을 제거 해준다.

- 사용법: 문자열.trim();

→ 알아서 왼쪽에 있는 공백, 오른쪽에 있는 공백을 다 제거 해준다. 하지만 가운데 있는 공백은 제거 해주지 않는다. 가운데 공백은 replace함수를 써서 제거 해줘야 한다.
