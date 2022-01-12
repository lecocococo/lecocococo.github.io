---
date: 2022-01-12
title: "[JavaSpring] POJO, DAO, DTO, VO?"
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

# <span style="color:#58ACFA">POJO</span>

- **POJO(plain Old Java Object)는 특별한 환경에 종속되지 않는 일반적인 단순 자바 객체**를 의미합니다.

# <span style="color:#58ACFA">DAO</span>

- **DAO(Data Access Object) 는 데이터베이스의 data에 접근하기 위한 객체**입니다. DataBase에 접근 하기 위한 로직 & 비지니스 로직을 분리하기 위해 사용합니다.

# <span style="color:#58ACFA">DTO</span>

- **DTO(Data Transfer Object) 는 계층 간 데이터 교환을 하기 위해 사용하는 객체로, DTO는 로직을 가지지 않는 순수한 데이터 객체(getter & setter 만 가진 클래스)입니다.**
- 사용자가 입력한 데이터가 DB까지 가는 과정
  - 유저가 브라우저에 데이터를 입력하면 데이터를 DTO에 넣어 전송합니다.
  - DTO를 받은 서버가 DAO를 이용하여 DB로 데이터를 집어넣습니다.

# <span style="color:#58ACFA">VO</span>

- **VO(Value Object)는 값을 위해 쓰이는 값 오브젝트입니다.** **read-Only 특징**을 가집니다.(DTO와 비슷하지만 DTO는 값이 변할 수 있습니다.)

## <span style="color:#58ACFA">참고</span>

<https://melonicedlatte.com/2021/07/24/231500.html>
<https://melonicedlatte.com/2021/08/21/234400.html>
<br/>
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
