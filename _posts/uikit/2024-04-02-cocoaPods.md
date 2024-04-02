---
title: "[UIKit] 코코아팟(cocoapods) 설치하기"
excerpt: "홈브루로 코코아팟(cocoapods) 설치"
  
categories:
  - UIKit
tags:
  - [swift, iOS, cocoapods]

permalink: /UIKit/cocoapods/ 
toc: true         
toc_sticky: true   
comments: true      
---

# 코코아팟(cocoapods)이란 ? 
- Objective-C 및 Swift Cocoa 프로젝트의 종속성 관리자
- 즉, CocoaPods은 Objective-C 또는 Swift에서 `라이브러리를 사용할 수 있게 도와주는 모듈`이다.

<br>

# 설치하기
## 1. 홈브루 버전 확인 및 업데이트 
- 터미널에서 홈브루 버전확인 및 업데이트를 합니다. 

```console
imhs@imhsui-MacBookPro ~ % brew --version 
Homebrew 4.2.11
imhs@imhsui-MacBookPro ~ % brew update
imhs@imhsui-MacBookPro ~ % brew --version
Homebrew 4.2.15
``` 

<br>

## 2. 코코아팟 설치 
- [코코아팟 홈페이지 바로가기](https://cocoapods.org/){:target="_blank"}
- 코코아팟 홈페이지에서 설치 명령어를 확인할 수 있습니다. 
- sudo gem install cocoapods

```console
imhs@imhsui-MacBookPro ~ % sudo gem install cocoapods
```

<br>

# 버전확인 
```console
imhs@imhsui-MacBookPro ~ % pod --version
1.15.2
```