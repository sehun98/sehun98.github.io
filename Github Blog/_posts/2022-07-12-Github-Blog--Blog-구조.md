---
title: "Github Blog : 블로그 구조"
excerpt: "Github Blog를 커스터마이징 하기 위해 구조를 파악합니다."
categories:
  - Github Blog
---

<br>

<br>

## home page

1. `index.html` 에서 `home_hero.html` 연결
   <br>
2. `_layouts/home_hero.html`
   <br>
3. `_layouts/archive.html`
   <br>
4. `_layouts/defult.html`
   <br>
5. `archive-single.html`
   <br>
6. `page__meta.html`
   <br>
7. `__breadcrumbs.html`
   <br>
8. `__sidebar.html`
   <br>
9. `__author-profile.html`
   <br>
10. `__author-profile-custom-links.html`
    <br>
11. `__head.html`
    <br>
12. `__seo.html`
    <br>
13. `__head/custom.html`
    <br>
14. `__skip-links.html`
    <br>
15. `__masthead.html`
    <br>
16. `__search/search-form.html`
    <br>
17. `__footer/custom.html`
    <br>
18. `__footer.html`
    <br>
19. `__script.html`
    <br>
20. `__search/lunr-search-scripts.html`
    <br>
21. `__analytics.html`
    <br>
22. `__comments-providers/scripts.html`
    <br>
23. `__excerpt_hero.html`
    <br>
24. `__hero__meta.html`
    <br>
25. `patinator.html`
    <br>
26. `page__date.html`
    <br>
27. `tag_list`
    <br>

<br>

<h1>post</h1>

1. `_post` 머릿말에서 `categories`를 연결
   <br>
2. `_data/navigation.xml` 에서 `_config.xml` 연결
   <br>
3. `_config.xml`에서 `layout : single` 연결
   <br>
4. `_layouts/single.html`
   <br>
5. `page__hero` 
   <br>
6. `nav_list`
   <br>
7. `toc.html`
   <br>
8. `page__taxonomy.html`
   <br>
9. `category-list`
   <br>
10. `page_date.html`
   <br>
11. `post_pagination`

<br>

<br>
