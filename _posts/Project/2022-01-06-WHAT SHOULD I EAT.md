---
date: 2022-01-06
title: "[Project] 오늘 점심 뭐 먹을래?"
categories: Project
tags: 프로젝트 react
toc: true
toc_sticky: true
toc_label: "페이지 목차"
comments: true
sidebar:
  nav: "main-sidebar"
---

<br/>
# <span style="color:#58ACFA">오늘 점심 뭐 먹을래?</span>

link: <https://lecocococo.github.io/what-should-i-eat/>

서버를 못돌려 아직은 사용할 수 없습니다.

=> sk 브로드밴드의 모뎀으로 인해 포트 포워딩이 불가능한 상황 발생했습니다.
같은 ip내에선 접속이 원활하나 외부ip에선 접속이 안되는 상황 입니다.

=> ngrok 사용 시도할 예정입니다.

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
