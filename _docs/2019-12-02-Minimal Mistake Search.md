---
title: "지킬블로그, Minimal Mistake 검색기능 추가하기"
date: 2019-12-02
comments: true
excerpt: "블로그에 검색기능을 추가하자"
categories: Markdown
author_profile: false
---
<!-- POST ID: L926rzqGa5 -->
<!--Language Button HTML -->
<span><a class="Jekyll"><i class="fab fa-github"></i> Jekyll</a><a class="JekyllVer">4.0.0</a></span>  <span><a class="YAML"><i class="fab fa-yammer"></i> YAML</a><a class="YAMLVer">1.2</a></span>  <span><a class="Liquid"><i class="fas fa-flask"></i> Liquid</a><a class="LiquidVer">4.0.0</a></span>
<!--Language Button HTML -->
<!-- Main content-->

블로그의 검색기능 구현을 위한 자바스크립트 코드를 생각하다 혹시나 싶어 검색을 해보았습니다. 역시 Minimal mistake는 블로그의 검색기능을 미리 구현해놓았습니다.  `_config.yml` 파일에서 검색기능을 On/Off 할 수 있습니다.

![L926rzqGa5_1](/assets/images/post/Jekyll/L926rzqGa5_1.png)

search 속성을 true로 설청하면 간단히 검색버튼과 기능을 구현할 수 있습니다(Lunr).

Minimal mistake 웹 페이지에 따르면 깃허브 페이지에 호스트 되는 사이트의 경우 검색기능은 기본적으로 Lunr에 100% 호환이 됩니다. 하지만, Algolia나 Google Custom Search Engine 사용자를 위한 설정 또한 존재합니다.

검색기능을 추가하면 페이지 우측 상단에 🔍 아이콘이 등장합니다. 검색기능은 새로운 페이지로 이동되지 않는다는 점이 인상적입니다.

![L926rzqGa5_2](/assets/images/post/Jekyll/L926rzqGa5_2.png)

검색바의 placeholder "Enter your search term..."이 조금 거슬립니다. 이 부분은 `/_includes\search.html`에서 수정할 수 있습니다.

![L926rzqGa5_3](/assets/images/post/Jekyll/L926rzqGa5_3.png)
<!-- Main content-->

<!-- Javascript -->

<!-- Javascript -->

<!-- CSS -->

<!-- CSS -->
