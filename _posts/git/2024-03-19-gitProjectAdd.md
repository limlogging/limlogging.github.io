---
title: "Xcode 프로젝트 깃허브(GitHub)에 추가하기" 
excerpt: "Xcode 프로젝트 깃허브(GitHub)에 추가하기"
categories: git
tags: [git, github, xcode, add, commit, push]

permalink: /git/gitProjectAdd/    
toc: true           
toc_sticky: true    
comments: true      #댓글
---

# 1. 원격 저장소 추가 
- GitHub에 새로운 원격 저장소를 생성하고 로컬 저장소에 해당 원격 저장소를 추가합니다.
![](/assets/images/categories/git/2024-03-19-gitProjectAdd1.png)

# 2. XCode 프로젝트 생성 
- Xcode 프로젝트의 이름과 GitHub 레포지토리의 이름이 반드시 같을 필요는 없습니다. 
![](/assets/images/categories/git/2024-03-19-gitProjectAdd2.png)

# 3. 터미널 오픈 
- 프로젝트 폴더에서 우클릭 후 터미널 오픈합니다. 
![](/assets/images/categories/git/2024-03-19-gitProjectAdd3.png)

# 4. git init - 저장소 초기화
- 명령어는 새로운 Git 저장소를 초기화하는 데 사용됩니다. 
- git init 
    - 해당 명령어로 현재 디렉토리에 새로운 Git 저장소를 만듭니다. 이 저장소에는 프로젝트의 모든 변경 내역을 추적하고 관리할 수 있는 .git 디렉토리가 생성됩니다.
```console
imhs@imhsui-MacBookPro MyTodoList % git init
```
```console
힌트 = : Using 'master' as the name for the initial branch. This default branch name
힌트: is subject to change. To configure the initial branch name to use in all
힌트 : of your new repositories, which will suppress this warning, call:
힌트 :
힌트 : git config -global init.defaultBranch ‹name>
힌트 : 
힌트 : Names commonly chosen instead of 'master' are 'main', 'trunk' and
힌트 : 'development'. The just-created branch can be renamed via this command:
힌트 :
힌트 : git branch -m <name>
/users/imhs/Desktop/내배캠 스파르타/실습과제/MyTodoList/.git/ 안의 빈 깃 저 장소를 다시 초기화했습니다 
```

# 5. git add . - 스테이징 영역에 추가 
- 명령어는 Git에서 변경된 모든 파일을 스테이징 영역에 추가하는 역할을 합니다. 
- git add . 
    - 현재 디렉토리 및 하위 디렉토리에서 변경된 모든 파일을 찾습니다.
    - 변경된 파일을 스테이징 영역에 추가합니다. 이는 Git이 해당 파일의 변경 내용을 추적하고, 다음 커밋에 포함시키기 위한 준비 단계입니다.
```console
imhs@imhsui-MacBookPro MyTodoList % git add . 
```

# 6. git commit -m "커밋메시지" - 저장소에 기록 
- 스테이징 영역에 추가된 파일은 git commit 명령어를 사용하여 커밋할 수 있습니다. 스테이징 영역에 추가된 파일은 이후 커밋에 반영되며, 커밋을 통해 변경 내용이 저장소에 영구적으로 기록됩니다.
- git commit -m "MyTodoList 추가" 
```console
imhs@imhsui-MacBookPro MyTodoList % git commit -m "MyTodoList 추가" 
```

# 7. git branch -M main - 기본 브랜치 이름 변경 
- 기본적으로 Git 저장소를 초기화하면 "master"라는 이름의 기본 브랜치가 생성됩니다. 그러나 최근의 표준화 노력과 함께 이를 "main"으로 변경하는 추세가 있습니다. 
- git branch -M main 명령어는 현재 작업 중인 브랜치를 "main"으로 변경합니다.
- git branch -M main 
```console
imhs@imhsui-MacBookPro MyTodoList % git commit -m "MyTodoList 추가" 
```

# 8. git remote add origin 저장소URL - git 저장소에 원격 저장소 추가 
- 현재 Git 저장소에 origin이라는 이름으로 URL의 원격 저장소를 추가
- git remote add origin https://github.com/limlogging/MyTodoList.git
```console
imhs@imhsui-MacBookPro MyTodoList % git remote add origin https://github.com/limlogging/MyTodoList.git
```

# 9. git push -u origin main - 작업 중인 브랜치를 원격 저장소에 푸시 
- 현재 작업 중인 브랜치를 원격 저장소에 푸시하는 역할을 합니다. 
- -u 옵션은 해당 브랜치를 원격 저장소의 기본 브랜치로 설정하는 역할을 합니다.
    - 이 옵션을 사용하면 이후에는 git push 명령어를 실행할 때 -u 옵션 없이도 동일한 원격 저장소 및 브랜치로 푸시할 수 있습니다.
- git push -u origin main
```console
imhs@imhsui-MacBookPro MyTodoList % git push -u origin main
```

# 10. 깃허브 확인 
- main 브랜치가 default로 생기고 commit 메시지도 확인할 수 있습니다. 
![](/assets/images/categories/git/2024-03-19-gitProjectAdd4.png)

# 11. 브랜치 새로 만들어서 작업 
- git branch로 현재 브랜치를 확인합니다.

```console
imhs@imhsui-MacBookPro MyTodoList % git branch
* main
```

- dev 브랜치를 만들고 생성된 브랜치로 이동합니다. 

```console
imhs@imhsui-MacBookPro MyTodoList % git checkout -b dev 
```

- 브랜치를 확인합니다. 

```console
imhs@imhsui-MacBookPro MyTodoList % git branch 
* dev
  main
```

- 작업 후 커밋합니다. 

```console
imhs@imhsui-MacBookPro MyTodoList % git add .
imhs@imhsui-MacBookPro MyTodoList % git commit -m "기능추가" 
imhs@imhsui-MacBookPro MyTodoList % git push origin dev
```