# Ones and Zeros

Instructions>

Given an array of ones and zeroes, convert the equivalent binary value to an integer.

Eg: `[0, 0, 0, 1]` is treated as `0001` which is the binary representation of `1`.

Examples:

```
Testing: [0, 0, 0, 1] ==> 1
Testing: [0, 0, 1, 0] ==> 2
Testing: [0, 1, 0, 1] ==> 5
Testing: [1, 0, 0, 1] ==> 9
Testing: [0, 0, 1, 0] ==> 2
Testing: [0, 1, 1, 0] ==> 6
Testing: [1, 1, 1, 1] ==> 15
Testing: [1, 0, 1, 1] ==> 11
```

However, the arrays can have varying lengths, not just limited to `4`.

**solution_1**

```java
import java.util.List;

public class BinaryArrayToNumber {

    public static int ConvertBinaryArrayToInt(List<Integer> binary) {
        // Your Code
      int total = 0;
      int currentValue = 1;
      for(int index = binary.size() - 1; index >=0; index--) {
        if(binary.get(index) == 1) {
          total += currentValue;
        }
        currentValue *= 2;
      }
      return total;
    }
}
```

binary.size()의 길이가 4라고 가정하고 Arrays.asList(1,1,1,1)이라 할 때

index  total            currentValue

3          1                      1x2

2         1+2                   2x2

1         1+2+4              2x2x2

0         1+2+4+8(15)   2x2x2x2

binary.size()의 길이가 4라고 가정하고 Arrays.asList(1,0,0,1)이라 할 때

index  total            currentValue

3          1                      1x2

2          0                      2x2

1          0                      2x2x2

0         1+2x2x2(9)       2x2x2x2

binary.size()의 길이가 4라고 가정하고 Arrays.asList(0,1,1,0)이라 할 때

index  total            currentValue

3          0                      1x2

2          2                      2x2

1          2+4(6)             2x2x2

0          0                     2x2x2x2

**solution_2**

```java
import java.util.List;

public class BinaryArrayToNumber {

    public static int ConvertBinaryArrayToInt(List<Integer> binary) {
      int total = 0;
      for (int i = 0; i < binary.size(); i++) {
        if (binary.get(i) == 1) total += Math.pow(2,binary.size() - i - 1);
      }
      return ans;
    }
}
```

binary.size()길이가 2라고 가정하고 Arrays.asList(1,1)일 경우

i         total

0      0+2^1  → 2^1 : 2^(2-0-1)

1      2+2^0 

```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

import static org.junit.Assert.*;

public class BinaryArrayToNumberTest {
    @org.junit.Test
    public void convertBinaryArrayToInt() throws Exception {

      assertEquals(1, BinaryArrayToNumber.ConvertBinaryArrayToInt(new ArrayList<>(Arrays.asList(0,0,0,1))));
      assertEquals(15, BinaryArrayToNumber.ConvertBinaryArrayToInt(new ArrayList<>(Arrays.asList(1,1,1,1))));
      assertEquals(6, BinaryArrayToNumber.ConvertBinaryArrayToInt(new ArrayList<>(Arrays.asList(0,1,1,0))));
      assertEquals(9, BinaryArrayToNumber.ConvertBinaryArrayToInt(new ArrayList<>(Arrays.asList(1,0,0,1))));

    }

} 
```
