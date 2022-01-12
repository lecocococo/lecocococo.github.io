---
date: 2022-01-12
title: "[JavaSpring] Spring Boot란?"
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

# <span style="color:#58ACFA">Spring Boot란?</span>

개발자는 스프링을 사용하기 위해서 다양한 설정을 직접 해줘야된다는 문제점이 있었고 개발자는 실행 환경, 의존성, 라이브러리등에 신경을 써주는데 시간을 사용했어야 했었습니다.<br/>

하지만 **Spring Boot를 사용하면 "그냥 실행할 수 있는" 독립 실행형 Spring 기반 애플리케이션을 쉽게 만들 수 있습니다.** 즉, 스프링을 좀더 사용하기 쉽게 만들어주는 역할을 합니다.

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
