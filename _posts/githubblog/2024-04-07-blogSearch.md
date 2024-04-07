---
title: "[minimal-mistakes]블로그 내 검색기능 추가하기 "
excerpt: "[minimal-mistakes] 블로그 내 검색기능 추가하기입니다."
categories: GitHubBlog
tags: [GitHub, blog, GitHub blog, 검색]

permalink: /GitHubBlog/search/  
toc: true           #On this page 보이기 
toc_sticky: true    #on this page 스크롤에 따라 움직이도록 
comments: true      #댓글
--- 
블로그에 검색 기능 추가하기입니다. 

# 1. _config.yml 파일 수정하기 
- _config.yml 파일에서 설정을 변경하면 바로 추가할 수 있습니다. 
- search 관련 설정을 true로 변경합니다. 

```yml
search                   : true # true, false (default)
search_full_content      : true # true, false (default)
search_provider          : lunr # lunr (default), algolia, google
lunr:
  search_within_pages    : true # true, false (default)
```

<br>

# 2. 확인 
검색기능이 추가되고 검색할 수 있습니다. 
![추가된 검색 기능 확인](../../assets/images/categories/githubblog/2024-04-07-blogSearch.png)