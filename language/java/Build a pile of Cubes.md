# Build a pile of Cubes

Instructions>

Your task is to construct a building which will be a pile of n cubes. The cube at the bottom will have a volume of n^3, the cube above will have volume of (n-1)^3 and so on until the top which will have a volume of 1^3.

You are given the total volume m of the building. Being given m can you find the number n of cubes you will have to build?

The parameter of the function findNb `(find_nb, find-nb, findNb)` will be an integer m and you have to return the integer n such as n^3 + (n-1)^3 + ... + 1^3 = m if such a n exists or -1 if there is no such n.

### **Examples:**

```
findNb(1071225) --> 45
findNb(91716553919377) --> -1
```

```
mov rdi, 1071225
call find_nb            ; rax <-- 45
mov rdi, 91716553919377
call find_nb            ; rax <-- -1
```

---

```java
public class ASum {
     
    public static long findNb(long m) {
        // your code
        long sum = 0;
        int n = 0;
        while (sum < m) 
            sum += (long) Math.pow(++n, 3);
        return sum == m ? n : -1;
    }
}
```

```java
import static org.junit.Assert.*;

import org.junit.Test;

public class ASumTest {

	@Test
	public void test1() {
		assertEquals(2022, ASum.findNb(4183059834009L)); 
	}
	@Test
	public void test2() {
		assertEquals(-1, ASum.findNb(24723578342962L)); 
	}
	@Test
	public void test3() {
		assertEquals(4824, ASum.findNb(135440716410000L)); 
	}
	@Test
	public void test4() {
		assertEquals(3568, ASum.findNb(40539911473216L)); 
	}
	
}
```

Math.pow()

- 거듭 제곱 구하기
- 자바에서 특정 값의 제곱을 구하려면 java.lang.Math 클래스의 pow()메소드를 사용
- Math.pow() 메소드는 입력 값과 출력 값은 모두 double형
- Math.pow(대상 숫자, 지수);