---
title: "Mac에서 github blog 만들기 - 1"
excerpt: "github blog 만들기"
categories: GitHubBlog
tags: [GitHub, blog, GitHub blog]

permalink: /GitHubBlog/start1/ #md 파일 제목과 다르게 url을 지정할 수 있음, 미지정 시 md 파일 명으로 따라감   
toc: true         #On this page 보이기 
toc_sticky: true  #on this page 스크롤에 따라 움직이도록 
---

# 개발자 블로그 ??? 

요즘 개발자들은 취업, 포트폴리오, TIL(Today I Learned) 등 각자의 이유로 블로그를 운영하고 있습니다. 저도 부트캠프를 계기로 개발자 블로그를 운영해보기로 하였습니다. 

네이버 블로그, 티스토리, 벨로그, 깃허브 블로그 등 다양한 플랫폼 중 깃허브 블로그를 선택하였습니다. <font style="text-decoration:line-through">(벨로그에 테스트로 글 두번 썼는데 제 마음에 들지 않았습니다.)</font>  


# GitHub 블로그 선택 이유
GitHub 블로그 장점은 찾아보니 3가지 정도로 구분할 수 있는 것 같습니다. 
1. 마음대로 꾸밀 수 있다. 
<br>블로그의 테마나 레이아웃부터 폰트, 컬러 등 본인의 취향껏 변경할 수 있습니다. 뿐만 아니라 다양한 기능도 추가할 수 있습니다.

2. GitHub 연동
<br>GitHub 블로그를 잘 가꾸는 것도 하나의 좋은 포트폴리오가 될 수 있습니다.

3. 광고 추가
<br>블로그에 **[Google AdSense](https://www.google.com/adsense/start/){:target="_blank"}**를 링크하여 광고 수익을 기대할 수 있습니다. 

저는 GitHub 사용 경험이 없어 Git, GitHub와 친해지기 위해 GitHub 블로그를 선택하였습니다. 

# GitHub 블로그 만들기 시작
## 1. 깃 설치하기 
블로그를 작성하게될 줄 모르고 설치 방법은 준비하지 못했으나 구글 검색을 통하여 충분히 설치하실 수 있으실겁니다. 
<br>[Git Download 바로가기](https://git-scm.com/downloads){:target="_blank"} 

## 2. 깃허브 회원가입 
[GitHub Homepage 바로가기](https://github.com/){:target="_blank"}

## 3. 깃허브 Repository 생성 
왼쪽 Top Repositories에서 New 버튼을 선택합니다. 
Repositories name은 꼭 "GitHub계정명.github.io"로 지정해야 합니다. GitHub Pages의 규칙 중 하나이며, 이 형식을 따르지 않으면 GitHub가 해당 저장소를 정적 사이트로 호스팅하지 않습니다.
![](/assets/images/categories/githubblog/GitHubBlogNewRepository.png)

## 4. Git clone 하기 
만들어진 Repository는 블로그를 만드는데 필요한 코드가 관리되는 곳입니다. Repository 생성 시 README.md 파일만 생성하여 저장소에 README.md 파일만 있습니다. 

로컬PC에서 블로그를 작성하고 GitHub 저장소에 등록하여 블로그를 작성하게 됩니다. 

그전에 저장소에 있는 README.md 파일을 로컬PC로 복사하도록 하겠습니다. 깃허브 Repository에 있는 파일을 내 로컬PC로 복사하는 작업을 clone이라고 합니다. 

로컬PC에서 GitHub 블로그를 작성할 폴더를 만듭니다. 
저는 바탕화면에 githubBlog 폴더를 만들었습니다.  
![](/assets/images/categories/githubblog/desktopGitHubBlogDirectoryCreate.png)

만들어진 폴더를 우클릭하여 폴더에서 새로운 터미널 열기를 실행합니다.
![](/assets/images/categories/githubblog/GitHubBlogDirectoryTerminalOpen.png)  

명령어로 git 폴더를 만들고 git 경로로 이동합니다. git 경로에서 repository에 있는 파일을 내PC로 복사하기 위해 git clone 깃주소를 입력합니다. 깃 주소는 아래 사진에서 확인하실 수 있습니다. 
![](/assets/images/categories/githubblog/GitHubBlogGitClone.png)
[](/assets/images/categories/githubblog/GitHubBlogGitCloneUrl.png)

git clone 명령어를 통하여 README.md 파일이 로컬PC에 복사된 것을 확인할 수 있습니다. 
![](/assets/images/categories/githubblog/GitHubBlogGitCloneSuccess.png) 

## 5. 로컬PC에 새로운 파일 만들고 Git Repository에 등록해보기 
Visual Studio Code 프로그램으로 GitHub.io 폴더를 열고 index.html 파일을 생성합니다. 
캡쳐는 HelloWorld.html로 만들었지만 index.html로 만드시면 저장소에 등록 후 페이지를 확인 할 수 있습니다. (https://깃허브ID.github.io/index.html)
![](/assets/images/categories/githubblog/GitHubBlogCreateFile.png)

1. 변경사항 저장 
새로 만든 html 파일을 저장하고 변경된 모든 내용을 저장하기위해 git add . 명령어를 입력합니다. 
```console
imhs@imhsui-MacBookPro limlogging.github.io % git add . 
```
2. 변경사항 확정 
git commit -m "변경사항 입력"
`commit`은 변경사항을 확정하는 것으로 변경사항에 대한 커멘트를 남겨(`-m "메시지"`) 나중에 무엇때문에 변경사항이 발생했는지 보기 쉽게 해줍니다. 
```console
imhs@imhsui-MacBookPro limlogging.github.io % git commit -m "파일 추가" 
```

3. GitHub 저장소에 업로드 
git push 명령어를 통해 저장소에 업로드 합니다. 
```console
imhs@imhsui-MacBookPro limlogging.github.io % git push 
```

# commit, push 시 에러 관련 
**Warning** 저는 git을 꽤 오래전에 설치하여 방치된 상태였습니다. 때문에 이메일 설정을 변경해야했고 깃허브 key 에러가 발생하였습니다. 
같은 에러가 발생하신다면 제가 본 블로그를 공유드릴테니 참고해보시기 바랍니다. 
<br>[git commit 후 author, email을 수정하는 방법](https://codedosa.com/1856){:target="_blank"}
<br>[git@github.com: Permission denied (publickey) 에러 해결 방법](https://medium.com/@su_bak/git-github-com-permission-denied-publickey-%EC%97%90%EB%9F%AC-%ED%95%B4%EA%B2%B0-%EB%B0%A9%EB%B2%95-76b0ab741c62){:target="_blank"}
{: .notice--warning}


# GitHub Repository 파일 업로드 확인 
GitHub 저장소에도 html 파일이 추가된 것을 확인 할 수 있습니다. 

이후 Ruby, Jekyll, bundler 설치, 테마를 다운로드 받아 로컬환경에서 실행하고 Repository에 등록이 필요한데 다음 포스팅에 작성해보도록 하겠습니다. 