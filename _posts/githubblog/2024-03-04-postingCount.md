---
title: "카테고리 옆 posting Count 추가하기 (minimal-mistakes)"
excerpt: "카테고리 옆 posting Count 추가하는 방법입니다."
categories: GitHubBlog
tags: [GitHub, blog, GitHub blog, Posting Count]

permalink: /GitHubBlog/postingCount/ #md 파일 제목과 다르게 url을 지정할 수 있음, 미지정 시 md 파일 명으로 따라감   
toc: true         #On this page 보이기 
toc_sticky: true  #on this page 스크롤에 따라 움직이도록 
--- 

# Posting Count 추가하기 
우여곡절 끝에 카테고리를 만들고 TEST 게시물을 작성하였는데요. 뭔가 허전해보여 생각했더니 Posting Count가 없었습니다. 

# 1. navigation.yml 수정하기 
children 하위에 category 항목을 추가합니다. 
``` yml
categories:
  - title: "iOS"    
    children: 
      - title: "Swift"
        url: /categories/swift/       
        category: "Swift"
      - title: "SwiftUI"
        url: /categories/swiftui/ 
        category: "SwiftUI"
  - title: "git" 
    children:
      - title: "Git"
        url: /categories/git/
        category: "git"
      - title: "GitHub Blog"
        url: /categories/GitHubBlog/
        category: "GitHubBlog"
  - title: "etc"
    children:
      - title: "내배캠 부트캠프"
        url: /categories/sparta/
        category: "sparta"
```

# 2. nav_list 수정 
아래 부분 코드를 주석하고  
```
{%raw%}
<li><a href="{{ child.url | relative_url }}"{% if child.url == page.url %} class="active"{% endif %}>{{ child.title }}</a></li> 
{% endraw %}
```
새로 코드를 추가합니다. 
```
{%raw%}
{% assign post_cnt = 0 %}
{% for category in site.categories %}
    {% if category[0] == child.category  %}
    {% assign post_cnt = category[1].size %}
    {% endif %}
{% endfor %}
<li><a href="{{ child.url | relative_url }}"{% if child.url == page.url %} class="active"{% endif %}>{{ child.title }}({{ post_cnt }})</a></li>
{% endraw %}
```

수정된 코드입니다. 
![](/assets/images/categories/githubblog/2024-03-04-postingCount.png)

# 3. 결과 확인 
카테고리 옆에 해당 카테고리의 전체 포스팅 수를 확인할 수 있습니다.  
![](/assets/images/categories/githubblog/2024-03-04-postingCountResult.png)

