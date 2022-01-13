---
date: 2022-01-12
title: "[JavaSpring] Java Spring Boot 프로젝트 생성"
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

# <span style="color:#58ACFA">Java Spring Boot 프로젝트 생성</span>

기본적으로 JDK와 IDE(VSCode, Intellij 등)은 컴퓨터 내부에 설치되있다고 생각하고 설명 하도록 하겠습니다.

**<span style="color:#58ACFA">1. Spring initializr</span>**

[Spring initializr](https://start.spring.io/)(링크)를 접속해줍니다. <br/>
Spring initializr에서는 Spring Boot를 위한 프로젝트 zip 파일을 다운받을 수 있습니다. 그리고 Spring에서 진행해야 되는 복잡한 프로젝트 설정을 간단한 옵션 선택을 통하여 바로 프로젝트를 생성할 수 있습니다.

![Spring initializr](/assets/images/spring initializr.png "Spring initializr")

- `project`
  => 앱이나 라이브러리를 컴파일, 빌드 및 패키징하기 위한 유연한 방법을 제공합니다.<br/>
  최근에는 Gradle을 많이 사용하는 추세입니다.
- `Language`
  => 개발에 사용할 프로그래밍 언어(Java, Kotlin, Groovy)를 선택할 수 있습니다.
- `spring boot`
  => spring boot의 버전을 선택하는 부분입니다.<br/>
  아직 개발중이거나 불안정한 버전은 뒤에 (SNAPSHOT)이 붙어있습니다.
- `group`
  => 여러가지 프로젝트들 사이에서 프로젝트를 식별하게 해주는 식별자, 고유한 이름을 적어주시면 됩니다.<br/>
  기본적으로 도메인 명을 거꾸로 사용합니다.
- `artifact`
  => 빌드 결과물의 이름을 적어주시면 됩니다.
- `name`
  => 기본적으로 artifact와 동일하게 적혀집니다.
- `packaging`
  => JAR 또는 WAR중에 골라서 선택해 주시면 됩니다.
- `java`
  => JDK버전에 맞추어 선택해주시면 됩니다.
- `dependencies`
  => 프로젝트에 사용되는 부가적인 기능을 위하여 사용하기 위한 Dependency 라이브러리를 선택해주시면 됩니다.
  (Spring Web, Spring Data JPA등은 거의 필수적으로 들어가게 되고 나머지 부분은 개발하시는것에 맞추어 넣어주시면 됩니다.<br/>
  참고할만한 사이트: [Spring Initializr를 통해 보는 스프링 각종 모듈 알아보기](https://appleg1226.tistory.com/11))

마지막으로 하단의 GENERATE를 클릭하여 Zip 파일을 다운 받아 주시면 됩니다.

**<span style="color:#58ACFA">2. IntelliJ에서 프로젝트 실행</span>**

다운받은 zip파일을 압축해제하고 IntelliJ에서 프로젝트를 실행하면 됩니다. 그러면 IntelliJ에서 자동으로 필요한 파일을들 다운받아줍니다.<br/>

그 후 java폴더 안의 java를 실행해주시면 됩니다. <br/>

Error 처리 방법:

- **Execution failed for task ':compileJava'.**

  1.  **File > Project Structure > Project > Project SDK**
      SDK버전이 내가 Spring Initialzr에서 설정한 것과일치 하는지 확인하고 바꿔주면 됩니다.
  2.  **File > Settings > Build Tools > Gradle**
      Gradle JVM 버전 설정을 설정하신 JDK로 맞춰주시면 됩니다.
  3.  **File > Settings > Compiler > Java Compiler**
      Project bytecode version이 맞는지 확인하시면 됩니다.

- **Error - Failed to configure a DataSource**

  1. **src > main > resources > application.properties**
     application.properties 파일에

  ```
  spring.datasource.driver-class-name=[JDBC 드라이버]
  spring.datasource.url=jdbc:[Database]://localhost:3306/[Database스키마]
  spring.datasource.username=[DB 아이디]
  spring.datasource.password=[DB 비밀번호]

  (예시)
  spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
  spring.datasource.url=jdbc:mysql://localhost:3306/[DB명]?useSSL=false& useUnicode=true&characterEncoding=utf8&serverTimezone=UTC
  spring.datasource.username=[DB접속ID]
  spring.datasource.password=[DB비번]
  ```

  를 추가해주시면 됩니다.

## <span style="color:#58ACFA">참고</span>

<https://melonicedlatte.com/2021/07/12/230800.html><br/>
<https://milenote.tistory.com/63><br/>
<https://7942yongdae.tistory.com/128><br/>
<https://devlimk1.tistory.com/149><br/>

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
