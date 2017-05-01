# thymeleaf-cheat-sheet
Spring + Thymeleaf 3 cheat-sheet

# About
For [Thymeleaf version 3.0](http://www.thymeleaf.org/doc/tutorials/3.0/usingthymeleaf.html)

Checked with Spring 4.3.8, Spring Boot 1.5.3 and Spring Security 4.2.2.

# Setting Up With Boot
TODO

# HTML5

Starter template:

```html
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org"
      xmlns:sec="http://www.thymeleaf.org/extras/spring-security">
      
<head>
    <title>Good Thymes Virtual Grocery</title>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
</head>

<body>
    <h1 th:text="'Hello ' + ${name}">Hello Wireframe</h1>
</body>

</html>
```

# General (Not Spring-specific)

| Description | Example |
|---|---|
| i18n messages | `<p th:text="#{home.welcome}">` |
| Unescaped i18n messages | `<p th:utext="#{home.welcome}">`|
