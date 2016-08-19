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
