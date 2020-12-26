# Credit Card Mask

Instructions>

Usually when you buy something, you're asked whether your credit card number, phone number or answer to your most secret question is still correct. However, since someone could look over your shoulder, you don't want that shown on your screen. Instead, we mask it.

Your task is to write a function `maskify`, which changes all but the last four characters into `'#'`.

```java
public class Maskify {
    public static String maskify(String str) {
        if(str.length()<4){
          return str;
        } else {
          String newStr ="";
          for(Integer i=0; i<str.length(); i++) {
            if(i>=4){
              newStr += "#";
            }
          }
					//마지막 4글자 // substring(시작위치)
          newStr += str.substring(str.length()-4); //str문자열 길이-4
          return newStr;
        }
    }
}
```

```java
import org.junit.Test;
import static org.junit.Assert.assertEquals;
import org.junit.runners.JUnit4;

public class SolutionTest {
    @Test
    public void testSolution() {
        assertEquals("############5616", Maskify.maskify("4556364607935616"));
        assertEquals("#######5616",      Maskify.maskify(     "64607935616"));
        assertEquals("1",                Maskify.maskify(               "1"));
        assertEquals("",                 Maskify.maskify(                ""));

        // "What was the name of your first pet?"
        assertEquals("##ippy",                                    Maskify.maskify("Skippy")                                  );
        assertEquals("####################################man!",  Maskify.maskify("Nananananananananananananananana Batman!"));
    }
}
```

---

### Substring 으로 문자열 자르기

- **String substring(int index)**

    첫 번째로 인자 값을 하나만 받는 함수. 인자 값은 int형으로 substring 하고자 하는 문자열의 앞에서 부터 몇 번째 위치 인가를 지정하는 값. 입력 받은 인자 값을 index로 해당 위치를 포함하여 이후의 모든 문자열을 리턴 시키는 함수.

- **String substring(int beginIndex, int endIndex)**

    첫 번째 입력 받는 인자 값은 인자 값이 한 개인 substring과 같이 가져올 문자열의 시작 부분을 지정.

    두 번째 입력 받는 인자 값은 가져올 문자열의 끝 부분을 지정 하는 것.

### Int VS Integer

- **Int(Primitive자료형-long,float,double..)**

    -산술 연산이 가능함

    -null로 초기화 할 수 없음.

- **Integer(Wrapper 클래스-객체)**

    -Unboxing을 하지 않으면 산술 연산이 불가능 하지만, null값을 처리할 수 있음.

    -null값 처리가 용이하기 때문에 SQL과 연동할 경우 처리가 용이함

    -DB에서 자료형이 정수형이지만 null값이 필요한 경우 VO에서 Integer를 사용할 수 있음.

- **int와 integer간의 변환**

    Boxing      : Primitive자료형 → Wrapper클래스

    Unboxing :  Wrapper클래스 → Primitive자료형