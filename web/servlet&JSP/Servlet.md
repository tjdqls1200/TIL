**Servlet**이란 클라이언트의 요청에 따라 **동적 페이지를 만들기 위한 자바 코드로 된 파일**로 WAS에 의해 Servlet Container에서 실행이 된다.



public class [       ] extends **HttpServlet** (HttpServlet 추상클래스의 **service라는 함수를 구현**)

```java
import javax.servlet.*;
import javax.servlet.http.*;
import java.io.*;

public class Example extends HttpServlet
{
  //HttpServletRequest 입력, HttpServletResponse 출력
    public void service (HttpServletRequest request,
            HttpServletResponse response) throws IOException, ServletException {
      // 서버에 출력 System.out.println("hello Servlet");
      
      // 클라이언트에 출력
      OutputStream os = response.getOutputStream();
      PrintStream out = new PrintStream(os, true);
      out.println("Hello Servlet!");
      
      // 단순 문자열 출력시 Writer 쓰는 게 더 간편
      PrintWriter out = response.getWriter();
      out.println("Hello Servlet!!");
    }
}
```

servlet 라이브러리가 기본 JDK에 있는 라이브러리가 아니라 톰캣에 설치된 라이브러리라서 컴파일시에 클래스 패스 경로를 추가해줘야 한다.

class path 컴파일 옵션 : -cp [servlet-api.jar 경로]

javac -cp /usr/local/Cellar/tomcat/9.0.43/libexec/lib/servlet-api.jar Example.java





**Servlet 클래스 파일은 어디에 있어야 하는가?**

/usr/local/Cellar/tomcat/9.0.43/libexec/webapps/ROOT/**WEB-INF/classes/**

톰캣 ROOT 내 WEB-INF에 있는 자원은 클라이언트에 의해 요청될 수 있는 디렉토리가 아니다. (서버쪽에서만 접근 가능)

web.xml에서 Servlet mapping을 하고 클라이언트는 매핑된 이름으로 url 요청을 하면 톰캣이 실행해줌

웹서버는 url 요청을 받고 파일이 없으면 WAS에게 넘김 -> WAS에서 매핑 정보를 조회하여 Servlet 실행

매핑 정보를 web.xml파일에서 설정해도 되지만 어노테이션을 이용하는 것이 더 좋음

web-app 에서 metadata-complete="false" 추가("true"일 경우 모든 설정을 web.xml에서만 확인) 

서블릿 출력 형식을 지정하지 않으면 브라우저는 각각에 따라 자의적으로 해석을 한다. (html 또는 text)

 

**IntelliJ로-JSP-프로젝트-생성**

https://velog.io/@ruddms936/IntelliJ로-JSP-프로젝트-생성



**톰캣 한글 깨지는 이유**

1. 웹서버에서 클라이언트로 보내는 단위가 ISO-8859-1인 유럽 인코딩 방식을 사용하는데 이는 1바이트씩 쪼개서 전달이 되는데 한글은 2바이트씩 전달이 되야 하기 때문에 한글이 깨짐
2. UTF-8(유니코드) 방식을 사용하여 2바이트씩 전달을 해도 브라우저가 다른 인코딩 방식으로 해석할 경우 한글이 깨짐

```java
// 인코딩 방식 UTF-8 으로 설정
response.setCharacterEncodong("UTF-8");
// text 형식과 인코딩 방식을 브라우저에 전달(브라우저가 이를 보고 인코딩 방식을 맞게 설정)
response.setContentType("text/html; charset=UTF-8");

```



클라이언트에서 웹서버에 url에 데이터를 실어 보내는 것을 Get 요청이라 하고 그 데이터는 QueryString방식으로 전송한다.

http://localhost/hello + **QueryString**

http://localhost/hello**?cnt=3** (3은 int 3이 아닌 String "3")

url에서 값을 직접 입력해서 보내기보단 html 태그로 값을 입력 받아서 get방식으로 전송

```html
<body>
    <div>
        <form action="hi"> //hi로 매핑된 servlet 파일 Get 요청
            <div>
                <label>"출력 횟수"</label>
            </div>
            <div>
                <input type="text" name="cnt">
                <input type="submit" value="출력">
            </div>
        </form>
    </div>
</body>
```



클라이언트에서 url에 실어 보낸 QueryString을 받으려면

request.getParameter("cnt");



회원가입 정보나 긴 문장의 게시글 같은 경우 get 방식으로 url에 실어 보내는 것은 옳지 않다.

이런 경우 post 방식으로 전송하면 데이터가 url이 아닌 바디에 포함되어 전송이 된다.

```html
<body>
    <div>
        <form action="notice_reg" method="post">
            <div>
                <label>제목 : </label>
                <input type="text" name="title">
            </div>
            <div>
                <lavel>내용 : </lavel>
                <textarea name="content"> </textarea>
            </div>
            <div>
                <input type="submit" value="등록">
            </div>
        </form>
    </div>
</body>	
```



**동적 페이지 생성 흐름**

1. 웹 서버는 **클라이언트에 요청**을 받으면 확인 후 웹 서버에 해당 데이터가 없으면 **WAS(Web Application Server)에 HTTPRequest를 요청**  
2. WAS는 웹 서버의 요청을 받고 **Servlet Container**에서 **HttpServletRequest, HttpServletResponse 객체를 생성**
3. 클라이언트에서 요청한 URL 데이터로 해당 **Servlet을 조회(web.xml 또는 Annotation 매핑 정보 조회)**
   - Servlet은 클라이언트로부터 최초 요청시에 **단 한번만 init() 초기화** (각 Servlet 객체는 Servlet Container에 하나만 존재)
   - 한번 호출된 Servlet은 Servlet Container에 남아 있어 **재요청시 init() 없이 바로 service() 메소드를 실행**하여 요청을 처리.
4. Servlet을 찾아 **Thread를 생성하고 service() 메소드를 실행**한다.
5. GET, POST 방식에 따라 **doGet() 또는 doPost() 메소드를 실행**하여 **동적 페이지를 생성**하고 HttpServletResponse에 전달
6. 클라이언트에 동적 페이지 전달,  **Thread 종료, HttpServletRequest, HttpServletResponse 객체 소멸**



https://dololak.tistory.com/47



**CGI -> Servlet -> JSP**

1. **기존의 웹 서버는 저장해둔 정적인 페이지를 전달하여 보여주는 것만 가능**했기 때문에 클라이언트의 요청에 따라 동적으로 페이지를 생성하고 이를 클라이언트에게 보내주는 것이 불가능. 
2. 따라서 **서버에서 외부 프로그램을 사용하여 동적인 페이지를 생성**하고 이를 클라이언트에게 전달할 수 있는 **CGI(Common GateWay Interface)**가 등장
3. 서버에서 Process 단위로 실행이 되는 CGI는 클라이언트의 요청이 많을때 서버에 부하가 크게 가게 되었고 Thread 단위로 실행되는 Servlet을 사용하여 성능을 개선 (후에 JSP 등장)



https://dololak.tistory.com/475



**상태 유지 방법 3가지 (Application, Session, Coockie)**

Application 저장소가 헬스장(공용 공간)이면 Session은 개인 사물함(시간 지나면 비움), Cookie는 개인 가방(분실 위험)

**Application (ServletContext)**

Servlet은 호출 시 Thread를 할당 받아 동작하는데 클라이언트에 동적 페이지를 전달하고 나면 Thread도 종료가 되면서 스택 메모리가 소멸이 된다. 그래서 값을 받아서 저장해둘 필요가 있는 경우 Servlet Contex라는 저장소를 사용한다. Servlet Context는 서블릿들이 자원(데이터)을 공유하는 공간으로 웹 어플리케이션마다 하나씩 존재하며 컨테이너 실행과 종료시에 생성 되었다가 소멸된다.

```java
ServletContext application = request.getServletContext();

application.setAttribute("value", x);	// ServletContext에 값을 저장
```

사용범위 : 전역 범위에서 사용

생명주기 : WAS가 시작해서 종료할 때까지

저장위치 : WAS 서버의 메모리





**Session**

```java
HttpSession session = req.getSession();
session.getAttribute();

session.setAttribute();
```



Session이란 현재 접속한 사용자를 의미하며 사용자마다 개별적으로 할당받는 공간

 각각의 웹 브라우저를 사용하면 서로 다른 사용자로 인식

WAS에서 사용자를 구별하는 방법

사용자 요청 -> 서블릿 실행 -> 처음 요청을 한 경우 사용자는 세션키(SID)가 없는 상태.(서버에 해당 세션을 위한 공간이 없음) -> 요청 종료 시 세션키(SID) 부여(웹 브라우저에서 보관) -> 다음 요청부터는 세션키(SID)로 접근 -> 웹 브라우저 종료 시 세션키도 소멸

세션 공간은 일정 시간이 지나면 소멸되고 setMaxInactivelnterval(int interval) 메서드를 통해 세션 타임아웃을 정수(초)로 설정 가능

WAS에 저장 (사용자마다 세션을 생성해줌)

사용범위 : 세션 범위에서 사용

생명주기 : 세션이 시작해서 종료할 때까지

저장위치 : WAS 서버의 메모리





**Cookie** 

Application, Session이 웹 서버 저장소라면 Coockie는 클라이언트 저장소

웹 브라우저는 요청 시에 헤더 정보(TCP/IP, header.. coockie)와 사용자 정보를 전송하고 서버는 다음과 같이 받을 수 있다.

```java
getHeader();
getCoockies();
getParameter();
```

쿠키는 Key와 Value 형태(String)로 값을 가지며 addCookie()로 쿠키 정보를 사용자에게 보낼 수 있다.

```java
// 쿠키 읽기
Cookie[] cookies = req.getCookies();


// 쿠키 저장
Cookie cookie = new Cookie("c", String.valueOf(result));
res.addCookie(cookie);
```

쿠키는 기본적으로 웹 브라우저의 메모리에 저장이 되어 웹 브라우저를 닫으면 같이 소멸되지만 setMaxAge 설정을 하면 외부 파일로 저장이 되어 웹 브라우저가 닫혀도 데이터가 유지되게 할 수 있다.

setPath를 설정해서 해당 경로로 들어올 때만 쿠키를 전송하도록 할 수 있다.

데이터가 오래 유지되어야 하는 경우에 주로 사용하고 보안상의 중요한 데이터는 쿠키로 전송 시 위험

사용범위 : 웹 브라우저별 지정한 path 범주 공간

생명주기 : 브라우저에 전달한 시간부터 만료 시간까지

저장위치 : 웹 브라우저의 메모리 또는 파일





김영한 강의 보고 다시 정리

https://devuna.tistory.com/23



**서버에서 페이지를 만들어 보여줘야 하는 동적인 페이지가 필요한 경우** (계산기에서 계속 숫자를 더해가면 숫자들이 3 + 5 + 2 ... 이런 식으로 나열이 되어 보여지는데 일반 html 파일로는 이렇게 실시간으로 값을 받아 동적인 페이지를 보여주는 것이 불가능)

서블릿에서 html 코드를 출력해서 할 수는 있지만 html 코드에 out.write("<html>"); 이런식으로 쭉 써야해서 굉장히 비효율적 -> Servlet처럼 자바에서 html 코드를 사용하는 것이 아니라 html에서 자바 코드를 사용하는 방법 -> JSP(Java Server Page)



JSP란 **HTML내에 자바 코드를 삽입하여 웹 서버에서 동적으로 웹 페이지를 생성**하여 웹 브라우저에 돌려주는 **서버 사이드 스크립트 언어**





**GET, POST 요청에 따라 받기**



if(req.getMethod().equals("GET")) {

} else if (req.getMethod().equals("POST")) {

}

service() 메소드 호출시 GET, POST 방식에 따라 doGet(), doPost()가 호출된다.

그래서 doGet(), doPost()를 각각 @Override해서 정의해도 된다.

