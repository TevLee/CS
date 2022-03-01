## String / StringBuilder / StringBuffer 의 차이
### 쟁점
+ 연산횟수
+ 멀티쓰레드 환경
+ Race Condition

1. String vs. StringBuilder/StringBuffer
- String은 불변(immutable)하다.
- 따라서, 데이터 값이 수정되면 새로운 객체가 할당된다.
```
String str1 = new String("Hello ");
str1 += "World" // 새로운 객체 할당
```
한편, 리터럴변수를 대입하여 String 객체를 생성하면 **String constant pool**에 객체가 생성되므로
아래 코드에서 StrA와 StrC는 같은 메모리를 참조한다.
```
String strA = "abc";
String strB = new String("abc");
String strC = "abc";
String strD = new String("abc");

System.out.println(strA==strB); //false
System.out.println(strA==strC); //true
System.out.println(strB==strD); //false
```

2. StringBuilder vs. String/StringBuilder
- StringBuilder는 동기화(synchronized)를 지원하지 않는다.
