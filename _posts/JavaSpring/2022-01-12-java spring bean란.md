---
date: 2022-01-12
title: "[JavaSpring] Spring Bean란?"
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

# <span style="color:#58ACFA">Spring Bean란?</span>

**Bean이란 Spring Ioc 컨테이너가 관리하는 자바객체를 빈이라고 합니다.**
<br/>
일반적인 자바 프로그래밍에서는 만든 Class를 new를 통해 생성하여 사용했었지만 Spring같은 경우에는 Spring에서 관리되는 자바 객체를 사용합니다.  
<br/>
Spring Framework에서는 `ApplicationContext.getBean()` 같은 메소드를 사용하여 Bean을 얻어 사용하게 됩니다.

## <span style="color:#58ACFA">Spring Bean을 Spring Ioc 컨테이너에 등록하는 방법</span>

**<span style="color:#58ACFA">1. Java Annotation 사용</span>**

- Spring에서 Bean을 등록하기 위해선 **@Bean, @Configuration, @Component**등의 어노테이션을 사용합니다.
- **@Bean과 같은 경우는 @Configuration과 함께 사용**되며 @Configuration을 클래스명 위에 명시해주고 내부를 @Bean을 통하여 등록해주어야합니다. 주로 사용되는 때는 개발자가 직접 제어가 불가능한 라이브러리를 사용하거나 초기에 설정을 위하여 활용할때 @Bean 어노테이션을 사용합니다.
- **@Component과 같은 경우는 개발자가 직접 작성한 Class를 Bean으로 등록하기 위한 어노테이션**입니다.  
   추가적으로 @Controller, @Service, @Repository 어노테이션이 존재하는데 이것들은 @Component 어노테이션의 구체화된 형태입니다.
  ![@Controller, @Service, @Repository](/assets/images/@Controller@Service@Repository.png "@Controller, @Service, @Repository")

## <span style="color:#58ACFA">참고</span>

<https://melonicedlatte.com/2021/07/11/232800.html>
<https://wildeveloperetrain.tistory.com/26>

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
