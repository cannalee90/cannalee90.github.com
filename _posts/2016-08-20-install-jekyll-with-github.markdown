---
layout: post
title:  "깃허브와 제킬 인스톨 및 커스터마이징"
categories: jekyll
---

항상 블로그를 시작하려고 생각만하다가 결국 `jekyll`을 사용해기로 마음먹고 시작하기로 했다. 루비온레일즈을 주로 사용하는 개발자이기 때문에 다른 환경셋팅은 필요하지 않고 `jekyll`만 인스톨한 다음 사용할 수 있을 줄 알았는데 생각보다 삽질을 많이하는 바람에 다시 몇가지를 기록하기로 한다. 일단 `ruby`, `bundler`, `jekyll`은 설치된 상태라고 가정하고 시작합니다.

제킬 프로젝트를 시작한다.

```
> jekyll new blog
```

테마를 설치하는 방법이 안나와서 테마를 클론 해온 다음 `_config.yml` 파일을 수정하는 식으로 진행하기로 했다.

테마에 있는 링크가 깃허브에 업로드 하면 깨지는 바람에 post링크를 수정 `post.url | prepend: site.baseurl`

font를 `noto sans`와 `open sans`를 사용하기 위해서 [css파일](https://gist.github.com/cannalee90/97f0d30643f570c1c637b2c639d99b54)을 추가하고 적용시킨다.

각종 css 파일을 수정하면 완성!

이미지 파일을 반응형으로 만들기 위해서는 추가할때는 아래와 같은 css를 추가하고 이를 이미지 태그에 매번 추가해주면 된다.

~~~
.img-responsive {
  max-width: 100%;
  height: auto;
}

![my-image](http://){:class="img-responsive"}
~~~

구글 애널리스틱은 다른 사이트에서 설치 하듯 똑같이 코드를 발급받는다. 그리고 모든 페이지에서 그 스크립트를 추가하기 위해서 `_includes` 폴더에 새롭게 html파일을 만들어준다.

~~~
script.html

<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

  ga('create', 'USER-ID', 'auto');
  ga('send', 'pageview');
</script>

~~~

그리고 공통적으로 포함되는 레이아웃에 다음과 같이 스크립트 파일을 추가한다.

```text
{% raw %}
{% include head.html %}
{% endraw %}
```

그리고 개발자 도구를 열어서 확인하면 다음과 같이 올라간걸 확인 할 수 있다.

![](http://i.imgur.com/tVa4Qu8.png)

중괄호를 이스케입 하기 위해서는 다음과 같이 사용하면 된다.

```text
{{ "{% raw " }}%}
{{ "{% endraw " }}%}
```
