---
title: "Github Blog : 하이퍼링크"
excerpt: "지저분한 밑줄 꼴도 보기 싫을 때"
categories:
  - Github Blog
---

<br>

<br>

# 하이퍼링크 밑줄 없애기

`_sass/minimal-mistakes/_base.scss` 경로에서 다음과 같이 수정합니다.

```scss
a {
	text-decoration: none;
	&:focus {
		@extend %tab-focus;
	}
}
```

<br>

<br>
