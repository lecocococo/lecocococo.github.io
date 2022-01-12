---
date: 2022-01-12
title: "[JavaSpring] Spring이란?"
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

# <span style="color:#58ACFA">Spring이란?</span>

스프링은 자바 기반의 웹 어플리케이션을 만들 수 있는 프레임 워크입니다. Java 개발자들은 Spring을 사용하여 웹서비스를 만들수 있습니다. 국내기업에선 많은 서비스들을 Spring을 이용하여 만들고 있습니다.
<br/>

**스프링의 구성**<br/>
![Overview of Spring Faremwork](/assets/images/spring-overview.png "스프링 프레임 워크의 구성")

**스프링 웹페이지**: [Spring 웹페이지](https://spring.io/)

<br/>
## <span style="color:#58ACFA">Spring의 특징</span>
- Spring은 자바 객체와 라이브러리들을 관리해줍니다.

- Spring은 객체를 가져와 사용하고 자바 객체를 Spring내에서 관리합니다. 그리고 자바 객체의 life cycle을 관리합니다.

- **제어의 역전(IOC, Inversion of Control)**

  - 일반적인 **자바 프로그램에서는 모든 작업을 사용자가 제어하는 구조**였습니다. 자바의 객체들이 객체를 직접 생성하여 메소드 호출을 하여 프로그램의 흐름을 결정합니다. 예를 들어 A 객체에서 B 객체에 있는 메소드를 사용하고 싶으면, B 객체를 직접 A 객체 내에서 생성하고 메소드를 호출하는 방식입나다.
  - 하지만 **IOC가 적용이되면 개체의 제어가 특별한 관리 위임 주체에게 넘어가게 되고 사용자는 객체를 직접 생성, 제어 하지 않게됩니다.**
  - **요약하자면 Spring에 제어를 위임하여 Spring이 객체를 만들어 넣고 => 의존성 객체의 메소드를 호출** 하는 구조가 됩니다.

- **의존성 주입(DI, Dependency Injection)**
  - **의존성을 줄이기 위하여** 어떤 객체A를 사용하는 주체B가 객체A를 직접 생성하는게 아니라 **객체A를 외부(Spring)에서 생성해서 사용하려는 주객체B에 넣어주는 방식**입니다.

## <span style="color:#58ACFA">참고</span>

<https://melonicedlatte.com/2021/07/11/174700.html>

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
