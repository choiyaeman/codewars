# Regex validate PIN code

Instructions>

ATM machines allow 4 or 6 digit PIN codes and PIN codes cannot contain anything but **exactly** 4 digits or exactly 6 digits.

If the function is passed a valid PIN string, return `true`, else return `false`.

solution_1

```java
public class Solution {

  public static boolean validatePin(String pin) {
    
    if (pin.length() == 4 || pin.length() == 6){
        // 1. 숫자로 변환해보기
        try{
          Integer.parseInt(pin);
          return true;
        } catch (Throwable t){
          return false;
        }
    } else {
      return false;
    }
  }

}
```

solution_2

```java
public class Solution {

  public static boolean validatePin(String pin) {
    // Your code here...
    boolean result = false;
    if(pin.length()==4 || pin.length()==6){
      if(pin.matches("^[0-9]*$")){
        result = true;
      }

    } else {
      return false;
    }
    return result;
  }

}
```

^ 으로 우선 패턴의 시작을 알림.
[0-9] 괄호사이에 두 숫자를 넣어 범위를 지정해줄 수 있음.
*를 넣으면 글자 수를 상관하지 않고 검사함.
$ 으로 패턴의 종료를 알림.

```java
import org.junit.Test;
import static org.junit.Assert.assertEquals;
import org.junit.runners.JUnit4;

public class SolutionTest {
    @Test
    public void validPins() {
        assertEquals(true, Solution.validatePin("1234"));
        assertEquals(true, Solution.validatePin("0000"));
        assertEquals(true, Solution.validatePin("1111"));
        assertEquals(true, Solution.validatePin("123456"));
        assertEquals(true, Solution.validatePin("098765"));
        assertEquals(true, Solution.validatePin("000000"));
        assertEquals(true, Solution.validatePin("090909"));
    }
    
    @Test
    public void nonDigitCharacters() {
        assertEquals(false, Solution.validatePin("a234"));
        assertEquals(false, Solution.validatePin(".234"));
    }
    
    @Test
    public void invalidLengths() {
        assertEquals(false, Solution.validatePin("1"));
        assertEquals(false, Solution.validatePin("12"));
        assertEquals(false, Solution.validatePin("123"));
        assertEquals(false, Solution.validatePin("12345"));
        assertEquals(false, Solution.validatePin("1234567"));
        assertEquals(false, Solution.validatePin("-1234"));
        assertEquals(false, Solution.validatePin("1.234"));
        assertEquals(false, Solution.validatePin("00000000"));
    }
}
```

다른 풀이)

```java
public class Validator {

	public static void main(String[] args) {
		String pin = "0630";
		System.out.println(validator(pin));
	}

	public static boolean validator(String pin) {
		if (pin.length() == 4 || pin.length() == 6) {
			char[] array = pin.toCharArray();
			for (int i = 0; i < array.length; i++) {
				if (array[i] >= '0' && array[i] <= '9') {
					continue;
				} else {
					return false;
				}

			}
		} else {
			return false;
		}
		return true;
//		return pin.length()==4 || pin.length()==6 && pin.matches("^[0-9]*$") ? true : false;
	}
}
```

- charAt(인수)

    인수번째의 문자를 읽어 낸다.

- Java String toCharArray()
    - 자바 toCharArray() 메소드는 문자열을 chart형 배열로 바꾼다.
    - 이 메서드는 새롭게 만들어진 문자 배열을 리턴한다.
    - String형 변수.toCharArray() : 문자열을 char형 배열로 바꾼다.
    - new String(배열) : char형 배열을 문자열로 바꾼다.
- Integer.parseInt(String s)
    - 숫자형의 문자열을 인자 값으로 받으면 해당 값을 10진수의 Integer형으로 반환 해줌.

    ex) Integer.parseInt("2020");

- Integer.parseInt(String s, int radix)
    - 숫자형의 문자열을 첫번째 인자 값으로 받고 변환할 진수값을 입력하면 해당 진수에 맞춰 Integer 형으로 반환해줌

    ex) Integer.parseInt("2020", 16);

참고)
https://regexr.com/
