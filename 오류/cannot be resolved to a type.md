## (javax.servlet.jsp.pagecontext) cannot be resolved to a type 오류

### 상황
 + Intellij에서 javax.servlet.jsp.pagecontext 클래스를 사용하려 했으나, 빨간줄이 뜸
 
### 원인 판단
 + java build path에 외부 라이브러리(tomcat)환경이 잡혀있지 않아서...

### 해결
 + 외부 라이브러리 등록
    - Eclipse ) properties > java build path > add library > server runtime 선택...
    - Intellij) project structure > module > project + > library > werver runtime 선택...
    - Spring - gradle) 
