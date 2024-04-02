---
title: "[UIKit] SDWebImage 설치하기"
excerpt: "SDWebImage 설치"
  
categories:
  - UIKit
tags:
  - [swift, iOS, SDWebImage]

permalink: /UIKit/SDWebImage/ 
toc: true         
toc_sticky: true   
comments: true      
---

# SDWebImage란 ? 
- SDWebImage는 Objective-C로 작성된 이미지 로딩 및 캐싱 라이브러리입니다. iOS 및 macOS에서 많이 사용되며, Swift에서도 사용할 수 있습니다.
- SDWebImage는 비동기 이미지 다운로드, 캐싱 및 관리를 처리하고, 메모리 사용량을 최적화하여 원활한 사용자 경험을 제공합니다.
- 또한 SDWebImage는 GIF 지원, 프로그레시브 다운로드, 이미지 처리 등의 기능을 제공합니다.
- SDWebImage는 iOS 개발 커뮤니티에서 오랫동안 사용되어 온 라이브러리 중 하나입니다.

<br>

# 사용방법 
## 1. 프로젝트 폴더로 이동해서 터미널 오픈
- 프로젝트 폴더로 이동해서 폴더를 우클릭하고 터미널을 오픈합니다. 

<br>

## 2. 명령어를 입력합니다. 
```console
imhs@imhsui-MacBookPro MyGithub % pod init
``` 

<br>

## 3. 프로젝트 폴더안에 Podfile 확인 
- 프로젝트 폴더 안에 Podfile이 생깁니다. 

![](/assets/images/categories/uikit/2024-04-02-SDWebImage1.png)

<br>

## 4. Podfile 더블클릭 
![](/assets/images/categories/uikit/2024-04-02-SDWebImage2.png)

<br>

## 5. Podfile 내 SDWebImage 추가 
- pod 'SDWebImage' 

![](/assets/images/categories/uikit/2024-04-02-SDWebImage3.png)

<br>

## 6. SDWebImage 설치 - pod install
![](/assets/images/categories/uikit/2024-04-02-SDWebImage4.png)

<br>

## 7.project 재시작 - .xcworkspace 파일을 열어야합니다. 
