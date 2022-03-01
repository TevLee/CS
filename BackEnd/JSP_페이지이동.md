## JSP(index.jsp) > JSP(main.jsp) 페이지 이동
1. 데이터가 없을 경우
 + response 객체에 이동할 페이지의 주소(main.jsp)를 담아 전송
> 클라이언트가 request(index.jsp)를 보냄
> 서버의 JSP(index.jsp)에서 response 객체에 main.jsp를 담아서 Redirection 함
> 클라이언트가 다시 request(main.jsp)를 보냄
> 서버가 main.jsp를 담아 response함
```
// index.jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
  <head>
    <title>Insert title here</title>
    <%
      response.sendRedirect("main.jsp");
    %>
  </head>
  <body>
  <h1>First page</h1>
  </body>
</html>

```
 
2. 데이터가 있을 경우
+ request 객체에 데이터를 set하고 main2.jsp로 forwarding함
> 클라이언트가 request(index2.jsp)를 보냄
> 서버의 JSP(index2.jsp)에서 request 객체에 데이터(member=100)를 담음
> JSP(main.jsp)로 forwarding 해줌

> JSP(main.jsp)에서는 데이터를 get해서 사용
```
// index2.jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>Title</title>
</head>
<%
    // Cookie 생성 (공백 포함시 에러)
    response.addCookie(new Cookie("name","Tev_Lee"));
    response.addCookie(new Cookie("tel","010-1234-5678"));

    request.setAttribute("member",100);
    pageContext.forward("main2.jsp");
%>
<body>

</body>
</html>
```
```
// main2.jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <h2>main2.jsp입니다. index2에서 넘어왔습니다.</h2>
    <a>
        <h3>
            값은 :
            <%=request.getAttribute("member")%>
        </h3>
        %>
    </a>
</body>
</html>
```
## Servlet > JSP 페이지 이동
1. 데이터가 있을 경우
+ 서블릿(.java)에서 데이터를 set하고, dispatcher를 사용해 표현할 view를 선정하여 dispatcher를 forwarding함
> request 객체에 데이터를 set
> dispatcher에 JSP(.jsp)를 담음
> 해당 view를 forwarding해줌
```
// 서블릿(.java) > doGet()
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        int data = 150;
        request.setAttribute("member",data);
        RequestDispatcher dispatcher = request.getRequestDispatcher("servlet1.jsp"); // servelt1.jsp를 view로 결정
        dispatcher.forward(request,response); 
    }
```

### 중요 쟁점
+ 데이터가 **없는** 경우에는 클라이언트가 리다이렉션(Redirection) 해야하므로 서버가 **response** 객체에 담아 클라이언트에게 전달함
+ 반면, 데이터가 **있는** 경우에는 서버에서 forwarding하므로 **request** 객체에 데이터를 
