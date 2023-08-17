---
title: "Github Blog : Table Of Contents"
excerpt: "한눈에 볼 수 있는 블로그를 만들어봅시다."
categories:
  - Github Blog
---

<br>

<br>

# TOC (Table Of Contents) 사용하기

우측 옆의 TOC 사용법에 대해 알아봅니다.

<br>

(방법1) 

포스트(post)에서 다음과 같이 수정합니다.

```scss
toc: true
toc_sticky: true
toc_label: "Github Blog"
```

<br>

(방법2)

 `_config.yml` 에서 같은 카테고리별 일괄로 설정 가능합니다.

```
  # Github Blog
  - scope:
      path: "Github Blog"
    values:
      layout: single
      author_profile: true
      read_time: true
      show_date: true
      comments: false
      share: false
      related: true
      toc: true
      toc_sticky: true
      toc_label: "Github Blog"
      sidebar:
        nav: "Github Blog"    
      header:
        overlay_color: "#50C878"
      categories:
        - Github Blog
```

<br>

<br>
