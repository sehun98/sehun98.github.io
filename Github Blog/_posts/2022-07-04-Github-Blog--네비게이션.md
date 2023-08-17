---
title: "Github Blog : 네비게이션"
excerpt: "우측 상단 네비게이션은 어떻게 만들고 연결해야 하나요??"
categories:
  - Github Blog
---

<br>

<br>

# 네비게이션 수정하기

`_pages` 경로에 `categories-archive.md` 페이지를 추가합니다.

```
title: "Study Archive"
permalink: /categories/
layout: categories
author_profile: true
```

<br>

`_data/navigation.yaml` 경로에서 다음과 같이 수정합니다.

```scss
  - title: "STUDY ARCHIVE"
    url: /categories/
```
<br>

<br>
