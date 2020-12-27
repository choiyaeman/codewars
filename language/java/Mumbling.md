# Mumbling

Instructions>

This time no story, no theory. The examples below show you how to write function accum:

The parameter of accum is a string which includes only letters from a..z and A..Z.

**Examples:**

```java
accum("abcd") -> "A-Bb-Ccc-Dddd"
accum("RqaEzty") -> "R-Qq-Aaa-Eeee-Zzzzz-Tttttt-Yyyyyyy"
accum("cwAt") -> "C-Ww-Aaa-Tttt"
```

---

```java
public class Accumul {
    
    public static String accum(String s) {
     // your code
      String result = "";
      for(int i=0; i<s.length(); i++) {
        char currentChar = s.charAt(i);
        for(int j=0; j<=i; j++) {
          if(j==0) {
            result += Character.toUpperCase(currentChar);  
          } else {
            result += Character.toLowerCase(currentChar);
        }
      }
        result += "-";
    }
      return result.substring(0, result.length()-1);
  }
}
```

```java
import static org.junit.Assert.*;
import org.junit.Test;

public class AccumulTest {

    private static void testing(String actual, String expected) {
        assertEquals(expected, actual);
    }
    @Test
    public void test() {
        System.out.println("Fixed Tests accum");
        testing(Accumul.accum("ZpglnRxqenU"), "Z-Pp-Ggg-Llll-Nnnnn-Rrrrrr-Xxxxxxx-Qqqqqqqq-Eeeeeeeee-Nnnnnnnnnn-Uuuuuuuuuuu");
        testing(Accumul.accum("NyffsGeyylB"), "N-Yy-Fff-Ffff-Sssss-Gggggg-Eeeeeee-Yyyyyyyy-Yyyyyyyyy-Llllllllll-Bbbbbbbbbbb");
        testing(Accumul.accum("MjtkuBovqrU"), "M-Jj-Ttt-Kkkk-Uuuuu-Bbbbbb-Ooooooo-Vvvvvvvv-Qqqqqqqqq-Rrrrrrrrrr-Uuuuuuuuuuu");
        testing(Accumul.accum("EvidjUnokmM"), "E-Vv-Iii-Dddd-Jjjjj-Uuuuuu-Nnnnnnn-Oooooooo-Kkkkkkkkk-Mmmmmmmmmm-Mmmmmmmmmmm");
        testing(Accumul.accum("HbideVbxncC"), "H-Bb-Iii-Dddd-Eeeee-Vvvvvv-Bbbbbbb-Xxxxxxxx-Nnnnnnnnn-Cccccccccc-Ccccccccccc");
    }
}
```

### **charAt(int index)**

- 입력 받은 index 번째 문자를 반환
- java에서 index 값은 항상 0에서 부터 시작

### String subString(int beginIndex, int endIndex)

- beginIndex 위치에서 시작하여 endIndex 전 위치까지의 값을 리턴

### Java Character - Character.toUpperCase() 함수

- toUpperCase() 함수는 입력 받은 인자 값을 영문 대문자로 변환하여 리턴

### Java Character - Character.toLowerCase() 함수

- toLowerCase() 함수는 입력 받은 인자 값을 영문 소문자로 변환하여 리턴