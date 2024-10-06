---
title: JSP&Servlet
date: 2024-10-06 10:45:00 +09:00
categories:
  - JAVA
tags:
  - JAVA
  - 이론
  - JSP
  - Servlet
---

# 서블릿(Servlet)

Servlet은 동적 웹 페이지를 만들 때 사용되는 자바 기반의 웹 애플리케이션 프로그래밍 기술.
Servlet은 웹 요청과 응답의 흐름을 간단한 메서드 호출만으로 체계적으로 다룰 수 있게 해준다.

서블릿은 서버에서 실행되다가 클라이언트가 요청을 보내면 해당 요청(request)을 수행 후 클라이언트에 결과(response)를 전송한다.

## 서블릿의 동작 과정

    1. 클라이언트 요청(request)
    2. HttpServletRequest, HttpServletResponse 객체 생성
    3. web.xml이 요청에 해당하는 서블릿 탐색
    4. 해당하는 서블릿에서 service() 메서드 호출
    5. doGet() 또는 doPost() 호출
    6. 동적 페이지 생성 후 ServletResponse 객체에 응답 전송
    7. HttpServletRequest, HttpServletResponse 객체 소멸

## 서블릿의 생명주기

    1. 클라이언트의 요청이 들어오면 요청에 해당하는 서블릿이 메모리에 있는지 확인하고, 없을 경우 init() 메서드를 호출하여 메모리에 적재한다. init()은 처음 한번만 실행되기 때문에 해당 서블릿에서 공통적으로 사용해야 하는 것이 있다면 init()을 오버라이딩 하여 구현하면 된다. 실행 중 서블릿의 내용이 변경될 경우, 기존 서블릿을 destroy()하고 init()을 통해 새로운 내용을 다시 메모리에 적재한다.
    2. init()이 호출된 후 클라이언트의 요청에 따라서 service() 메소드를 통해 요청에 대한 응답이 doGet()과 doPost()로 분기된다. 이 때 서블릿 컨테이너가 클라이언트의 요청이 오면 가장 먼저 처리하는 과정으로 생성된 HttpServletRequest, HttpServleResponse에 의해 request와 response 객체가 제공된다.
    3. 컨테이너가 서블릿에 종료 요청을 하면 destroy() 메소드가 호출되는데 마찬가지로 한번만 실행되며, 종료시에 처리해야 하는 작업들은 destroy() 메소드를 오버라이딩하여 구현하면 된다.


# JSP

JSP(Java Server Pages)는 동적 웹페이지를 개발하기 위한 프로그래밍 기술로, Java를 사용하여 서버측에서 웹 페이지를 생성해 웹 브라우저로 전송해준다.

JSP파일은 HTML 구조에 JSP요소가 혼합된 형태이다.
## JSP의 장점

+ 짧은 코드로 동적인 웹 페이지를 생성
+ 기본적인 예외는 자동으로 처리
+ 많은 확장 라이브러리를 사용할 수 있다.
+ 스레드 기반으로 실행되어 시스템 자원을 절약

## JSP 구조

### 지시어

```html
  <%@ page language="java" contentType="text/html; charset=UTF-8"
      pageEncoding="UTF-8"%>
  <%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
  <%@ taglib prefix="pageNav" tagdir="/WEB-INF/tags" %>
```
JSP페이지를 서블릿으로 변환하는데 필요한 정보를 JSP엔진에게 알려주는 부분,
주로 스크립트 언어나 인코딩 방식 등을 설정

지시어 종류
+ page : JSP 페이지에 대한 정보를 설정하는 지시어
+ include : 외부 파일을 현재 JSP 파일에 포함시키는 지시어
+ tagdir : 표현 언어(EL)에서 사용할 자바 클래스나 JSTL을 선언하는 지시어

### 스크립트 요소

용도에 따라 3가지로 분류

+ 선언부

  표현식,스크립틀릿에서 사용할 변수나 메서드를 선언한다.

  사용 방법
  ```
    <%! 변수나 메서드 선언 %>
  ```

+ 스크립틀릿에서

  실행해야할 Java 코드를 작성

  사용 방법
  ```
    <% 실행할 Java 코드 %>
  ```

+ 표현식

  화면에 값을 하나씩 표현해줄 때 사용

  사용 방법
  ```
    <%= 표현해줄 값 %>
  ```

  # Servlet와 JSP의 차이

  | Servlet | JSP |
  | :---: | :---: |
  | Java 코드 안에  Html | Html 안에 Java 코드 |
  | MVC패턴에서 컨트롤러(controller) 만들때 사용 | MVC패턴에서 뷰(view) 만들때 사용 |


