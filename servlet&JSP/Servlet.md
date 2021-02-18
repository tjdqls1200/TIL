서블릿 코드는 WAS에 의해 실행이 되고 결과를 반환한다.



public class [       ] extends HttpServlet (HttpServlet 추상클래스의 service라는 함수를 구현)

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

/usr/local/Cellar/tomcat/9.0.43/libexec/webapps/ROOT/WEB-INF/classes/

톰캣 ROOT 내 WEB-INF에 있는 자원은 클라이언트에 의해 요청될 수 있는 디렉토리가 아니다. (서버쪽에서만 접근 가능)

servlet mapping을 통해 매핑을 하고 클라이언트는 매핑된 이름으로 url 요청을 하면 톰캣이 실행해줌

웹서버는 url 요청을 받고 파일이 없으면 WAS에게 넘김 -> WAS에서 매핑 정보를 조회하여 넘겨줌

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



흐름

1. 웹 서버는 **클라이언트에 요청**을 받으면 확인 후 웹 서버에 해당 데이터가 없으면 **WAS(Web Application Server)에 HTTPRequest를 요청**  

2. **WAS**는 웹 서버의 요청을 받고 **Servlet Container**에서 **HttpServletRequest, HttpServletResponse 객체를 생성**

3. 클라이언트에서 요청한 URL 데이터로 해당 Servlet을 찾음(web.xml 또는 Annotation)

4. Servlet을 찾아 service() -> doGet() or doPost() -> 동적 페이지 생성 -> HttpServletResponse로 전달

   

https://dololak.tistory.com/47

https://sjh836.tistory.com/126

https://myblog.opendocs.co.kr/archives/425

https://webfirewood.tistory.com/38