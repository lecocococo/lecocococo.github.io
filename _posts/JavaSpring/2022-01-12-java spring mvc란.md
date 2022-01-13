---
date: 2022-01-12
title: "[JavaSpring] Spring MVC란?"
categories: JavaSpring
tags: Java Spring Springboot
toc: true
toc_sticky: true
toc_label: "페이지 목차"
comments: true
sidebar:
  nav: "main-sidebar"
---

<br/>

# <span style="color:#58ACFA">Spring MVC란?</span>

**웹 애플리케이션 개발에 있어 MVC 패턴을 적용할 수 있도록 Spring에서 제공하는 프레임워크입니다.**
Spring MVC 프레임 워크는 Model, View, Controller로 모듈의 분리를 가능하게하고 애플리케이션 통합을 원활하게 처리가능합니다.

# <span style="color:#58ACFA">Spring MVC 구조</span>

![Spring MVC Architectur](/assets/images/springmvc-architectur.png "Spring MVC 구조")
Model, View, Controller로 모듈을 분리한 디자인 패턴

- **Model**
  - **뷰가 렌더링하는데 필요한 데이터입니다.**
  - 일반적으로 POJO로 구성됩니다.
  - Bean이 이에 해당합니다.
- **View**
  - **View는 실제로 보이는 부분입니다.**
  - 모델을 사용해 렌더링합니다.
  - 뷰는 JSP, JSF, PDF, XML등으로 결과를 표현합니다.
- **Controller**
  - **사용자의 행동에 응답하는 컴포넌트입니다.**
  - **컨트롤러는 모델을 업데이트하고 사용자의 요청에따라 적절한 결과를 Model에 담아 DispatcherServlet에게 전달해 주는 역할**을 합니다.
  - 주로 Servlet이 이 역할을 합니다.
    > (Servlet이란? Servlet은 웹 요청(Request)과 응답(Response)의 흐름을 간단한 메서드 호출만으로 체계적으로 다룰 수 있게 해주는 웹 애플리케이션 컴포넌트 또는 기술입니다.)

# <span style="color:#58ACFA">Spring MVC 흐름</span>

**Request → DispatcherServlet (web.xml) → Controller → Logic처리(service, db접근) → View 전달 → response**

- **DispatcherServlet**
  - 모든 request를 받습니다.
  - request를 실제로 처리할 Controller(Servlet)에게 클라이언트의 요청을 전달하고, controller가 리턴한 결과값을 View에게 전달하여 알맞은 응답 생성합니다.

# <span style="color:#58ACFA">Spring MVC와 Spring Boot차이</span>

1. 초기 설정의 자동화

- Spring MVC 구조의 경우 XML 파일들에 Dispatcher Servlet, Handler Mapping, View Resolver 등 설정들을 해줘야합니다.
- 하지만 Spring Boot같은 경우는 어노테이션을 적절히 사용한다면 Spring이 자동으로 처리하여줍니다.

2. WAS 내장 유무

- Spring MVC내에는 WAS이 내장 되어있지 않기 때문에 따로 Tomcat과 같은 WAS서버를 설치해줘야합니다.
- 하지만 Spring Boot 같은 경우에는 Tomcat이 내장 되어있어 따로 설치 하지 않아도 됩니다.

**실제로 둘은 같은 비교선상에 놓기에는 좀 힘들다고 봅니다. Boot는 스프링 프레임워크 자동화 도구이고 MVC는 말그대로 패턴이기 때문입니다.**

## <span style="color:#58ACFA">참고</span>

<https://gmlwjd9405.github.io/2018/12/20/spring-mvc-framework.html><br/>
<https://codingnotes.tistory.com/17><br/>
<https://dawoonjeong.com/spring-spring_mvc-vs-spring_boot-vs-spring_mvc/><br/>
<https://kyun-s-world.gitbook.io/nowstart/spring/springframeworkcore/0-spring-vs-spring-boot><br/>
<https://velog.io/@hellonayeon/springmvc-vs-springboot><br/>

{% if page.comments %}

<div id="disqus_thread"></div>
<script>
    /**
    *  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
    *  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables    */
    var disqus_config = function () {
        this.page.url = "{{ page.url | absolute_url }};";  // Replace PAGE_URL with your page's canonical URL variable
        this.page.identifier = "{{ page.id }}";; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
    };
    (function() { // DON'T EDIT BELOW THIS LINE
        var d = document, s = d.createElement('script');
        s.src = 'https://lecocococo-blog.disqus.com/embed.js';
        s.setAttribute('data-timestamp', +new Date());
        (d.head || d.body).appendChild(s);
    })();

</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
{% endif %}
