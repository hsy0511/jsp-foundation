# jsp-
# jsp 기초문법
## 1. jsp(Java Server Pages)란?
jsp는 기본적으로 html에서 자바코드를 넣어 실행된다.

그래서 사용할 때 대부분 변수 선언, 메서드 선언, 로직(논리)등은 자바 언어로 사용한다.

하지만 자바 코드를 html에서 사용할 때 필요한 문법이 있다.
## 2. jsp 스크릿틀릿
스크릿틀릿은 <% %>로 사용하는 태그이고, jsp 문법에서 가장 기초적인 태그이다.

대부분 jsp 문법을 스크릿틀릿을 기본으로 쓴다. 

```jsp
<% // 스크릿틀릿  %>
<% int a = 5; %>
<% int b = 5; %>
<% if(5>1){
	System.out.println("5는 1보다 크다");
}%>
```
## 3. jsp 선언부
선언부는 <%! %>로 사용하고 변수,메소드 등을 선언할때 사용하는 태그

```jsp
<% // 선언부 %>
<%! String name = "홍길동"; %>
<%! public int plus(int a, int b){ return a+b;} %>
```
## 4. jsp 표현부
표현부는 <%= %>로 사용되고 스크릿틀릿과 선언부에서 사용한 문법의 결과를 표현한다.

```jsp
<% // 표현부 %>
<p><%= name %></p>
<p><%= plus(5,5) %></p>
```
## 5. jsp 지시어
jsp 지시문은 서블릿 (동적 웹 페이지를 만들 때 사용되는 자바 기반의 웹 애플리케이션 프로그래밍 기술) 클래스의 전체 구조에 영향을 준고,

jsp 파일을 어떻게 처리할지 정보 등을 기술한다.

![image](https://user-images.githubusercontent.com/104752580/234434624-21757533-7f6f-4096-8901-dad898ce8393.png)

지시어에는 page, include, taglib 등이 있는데, 여기서 우리가 가장 많이 사용하는 page와 include를 알아보자.
## 5-1. 지시어 page
지시어 page는 jsp 엔진에게 jsp 파일에 대한 정보를 알려주는 역할을 한다.

page 속성을 알아보자.

![image](https://user-images.githubusercontent.com/104752580/234434990-038c31a6-6f83-4fa7-be68-28da6ff864df.png)

page 속성은 이러한 것들이 있다. 하지만 우리가 대표적으로 사용하는 속성 3개만 알아보자.

### 첫번째는 contentType이다.
contentType은 jsp 페이지가 생성할 문서의 타입을 지정하는 것이다.

예제를 보며 살펴보자.

```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
```

여기서 contentType이 text/html 이므로 html 문서 타입으로 페이지를 작성하겠다는 내용이 된다.
#### ※ utf-8 (Unicode Transformation Format - 8bit) : 가변 길이 유니코드 인코딩
### 두번째는 improt이다.
import는 jsp 페이지에서 자바의 클래스를 사용하기 위해서 사용하는 것이다.

예제를 보며 살펴보자.

```jsp
<%@ page import="java.sql.*" %>
```

여기서 import는 java sql 클래스를 사용하기 위해서 임폴트한 것이다.

### 세번째는 pageEncoding이다.
pageEncoding은 jsp 파일 작성시의 문자코드를 지정하기 위한 속성이다.

예제를 보며 살펴보자

```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
```

여기서 pageEncoding을 utf-8로 지정했기 때문에 문서코드가 한글로 지정된 것으로 볼 수 있다. 

만약 여기서 utf-8이 아니고 ms949로 지정하게 되면 웹 페이지에서 한글이 글자깨짐 현상이 일어난다.

## 5-2. 지시어 include
지시어 include는 가져올 파일의 경로를 넣어 다른 파일을 가져와 현재 파일에 뿌려주는 역할을 한다.

바로 예제를 살펴보자

![image](https://user-images.githubusercontent.com/104752580/234438355-0d60fe06-28c7-4b46-95b4-4327e86c06b3.png)

같은 폴더에 두개의 jsp 파일을 만들었다.

![image](https://user-images.githubusercontent.com/104752580/234438425-ee587995-72ac-495e-b332-e0c66f7279eb.png)

ex1.jsp 파일에 <%@ include file="ex.jsp" %>를 하며 ex1.jsp 파일에 ex.jsp 파일을 뿌려넣은 것이다.

## 6. jsp 액션태그 
액션태그는 jsp 문서에서 간다하게 다양한 구현을 할 수 있도록 만든 태그이다.

액션태그를 알아보자.

![image](https://user-images.githubusercontent.com/104752580/234439886-22ab2d91-e934-4960-a2f7-9859dcf47bba.png)

액션태그에는 이러한 것들이 있다. 하지만 우리가 대표적으로 사용하는 태그 2개만 알아보자.

### 첫번째는 jsp:include이다. 

앞서 설명했던 include file과 비슷한 기능을 가지고 있다.

예제를 보며 살펴보자

![image](https://user-images.githubusercontent.com/104752580/234440457-9fa4cccd-f3be-48e1-b4e0-1b32a47c1f88.png)

같은 폴더 안에 두개에 페이지을 만들었다.

![image](https://user-images.githubusercontent.com/104752580/234440498-1b78d527-4074-44e0-8c91-f546082bcadc.png)

ex1.jsp 페이지에 <jsp:include page="ex.jsp">를 사용하여 ex1.jsp 페이지에 ex.jsp 페이지를 포함한 것이다.

### 두번째는 jsp:forward이다.

jsp:forward는 현재 페이지에서 다른 페이지로 이동할 때 사용하는 태그이다.

예제를 보며 살펴보자

![image](https://user-images.githubusercontent.com/104752580/234441165-5a2444fe-303d-44cf-bc07-a704a8812d63.png)

같은 폴더 안에 두개에 페이지을 만들었다.

![image](https://user-images.githubusercontent.com/104752580/234441270-41c0d0f0-fda1-4deb-bf3b-81e89e9225c8.png)

ex1.jsp 페이지에 <jsp:include page="ex.jsp">를 사용하여 ex1.jsp 페이지에서 ex.jsp 페이지로 이동한 것이다.
## 7. jsp 주석
jsp에서 주석 처리는 "<%-- --%>" 이렇게 표현합니다.
```jsp
<%-- hello world!! --%>
<% out.println("hello world!!") %>
```
## 8. 서블릿
서블릿은 jsp와 비슷한 개념으로 동적 웹페이지를 제작할 때 사용되는 자바 기반의 웹 애플리케이션 프로그래밍입니다.

서블릿에 대해서 간단하게 예제를 살펴보겠습니다.
```java
package test;
import java.io.IOException;
import java.io.PrintWriter;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

@WebServlet("/hello")
public class HelloServlet extends HttpServlet {

	private static final long serialVersionUID = 1L;
       
	public HelloServlet() {
		super();
	}

	protected void doGet(HttpServletRequest request, HttpServletResponse response) 
    	throws ServletException, IOException {
		
		response.setContentType("text/html;charaset=utf-8");
		PrintWriter out = response.getWriter();
		out.println("<h1>Hello World!</h1>");
		out.close();
	}

	protected void doPost(HttpServletRequest request, HttpServletResponse response) 
    	throws ServletException, IOException {		
		doGet(request, response);
	}
}
```
![image](https://github.com/hsy0511/jsp-/assets/104752580/a72a597b-1352-4d7a-b22e-cbca759f2742)

hello world!를 보여주는 페이지입니다. 서블릿도 자바기반으로 만들어지는 웹 제작 프로그램인 것을 볼 수 있습니다.
## 9. 서블릿과 jsp 차이점
JSP는 클라이언트에 보여지는 결과 페이지를 생성할 때 주로 쓰이며, 서블릿은 UI 요소가 없는 제어나 기타 처리 용도로 쓰인다.
###### ※ 클라이언트: 네트워크로 연결된 서버로부터 정보를 제공받는 컴퓨터
###### ※ UI: 사용자가 사용하는 서비스나 제품의 화면 안에 모든 것을 의미
![image](https://github.com/hsy0511/jsp-/assets/104752580/54ca583c-53d2-4d2a-b0eb-7c604ec12f15)
###### ※ 컨트롤러: 사용자와 응용 프로그램 간의 중재자 역할
###### ※ 뷰: 사용자에게 접근이 허용된 자료만을 제한적으로 보여주기 위해 하나 이상의 기본 테이블로부터 유도된, 이름을 가지는 가상 테이블
## 10. jsp 실행과정
![image](https://github.com/hsy0511/jsp-/assets/104752580/2e4518d1-2457-4ad1-9a24-d52120c9b9c1)

WAS를 통해서 웹 브라우저의 HTTP 요청에 알맞은 JSP를 실행하고 그 결과를 HTTP 응답으로 웹 브라우저에 전송하게 됩니다.
###### ※ WAS : 웹 브라우저의 HTTP 요청에 알맞은 JSP를 실행하고 그 결과를 HTTP 응답으로 웹 브라우저에 전송한다.
## 11. jsp 페이지 기능

