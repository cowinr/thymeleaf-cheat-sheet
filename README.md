# Thymeleaf Cheat Sheet
Spring + Thymeleaf 3 cheat-sheet

# About
For [Thymeleaf version 3.0](http://www.thymeleaf.org/doc/tutorials/3.0/usingthymeleaf.html)

Checked with:

| Library | Version |
| --- | --- |
| Spring | 4.3.8 |
| Spring Boot | 1.5.3 |
| Spring Security | 4.2.2 |
| thymeleaf | 3.0.4 |
| thymeleaf-layout-dialect | 2.2.1 |
| thymeleaf-extras-springsecurity4 | 3.0.2 |
| thymeleaf-extras-java8time | 3.0.0 |

# Setting Up With Spring Boot

```xml
<dependencies>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-thymeleaf</artifactId>
    </dependency>
 
    <dependency>
        <groupId>org.thymeleaf.extras</groupId>
        <artifactId>thymeleaf-extras-springsecurity4</artifactId>
    </dependency>
 
    <dependency>
        <groupId>org.thymeleaf.extras</groupId>
        <artifactId>thymeleaf-extras-java8time</artifactId>
    </dependency>
</dependencies>
```

# HTML5

Starter template for defining a layout:

```html
layout.html
<html xmlns:layout="http://www.ultraq.net.nz/thymeleaf/layout"
      xmlns:th="http://www.thymeleaf.org"
      xmlns:sec="http://www.thymeleaf.org/extras/spring-security">
 
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <!--/* Title from any views that use this template is appended to this title. */-->
    <title layout:title-pattern="$LAYOUT_TITLE &raquo; $CONTENT_TITLE">Main Title</title>
</head>

<body>
    <h1 th:text="'Hello ' + ${name}">Hello Wireframe</h1>
    <section layout:fragment="content">
        Page content here...
    </section>
</body>

</html>
```

Starter template for a view using this layout:

```html
Page
<html xmlns:th="http://www.thymeleaf.org"
      xmlns:sec="http://www.thymeleaf.org/extras/spring-security"
      xmlns:layout="http://www.ultraq.net.nz/thymeleaf/layout"
      layout:decorate="~{layout}">
```

# General (Not Spring-specific)

| Description | Example |
|---|---|
| i18n messages | `<p th:text="#{home.welcome}">` |
| Unescaped i18n messages | `<p th:utext="#{home.welcome}">`|

# Spring Dialect

```html
<form method="post" th:object="${obj}" th:action="@{/obj/save/}">
<input type="hidden" th:field="*{id}" th:if="*{id ne null}"/>
<li th:each="err : ${#fields.allErrors()}" th:text="${err}">Error text for each field is listed here...</li>
<input type="radio" name="targeting" value="user" th:checked="*{targetUser ne null}" checked="checked"/>
<select class="form-control" th:field="*{type}">
    <option th:each="aType : ${allTypes}"
        th:value="${aType}"
        th:text="${aType}">Notices</option>
</select>
```

# Spring Security

```html
sec:authorize="hasAuthority('MY_XYZ')"
<span sec:authentication="name">username</span>
<a th:href="@{/messages/copy/{msgId}(msgId=*{id})}"
                th:if="*{id ne null}"
                sec:authorize="hasAuthority('MY_AUTHORITY')">
                Button
</a>
```

# Temporals (Java 8 date time API)

```html
<td th:text="${#temporals.format(obj.createdDate, 'dd/MM/yyyy')}">01/01/2001</td>
```
