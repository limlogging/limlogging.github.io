---
title: "[UIKit] 알라모파이어(alamofire) 설치하기"
excerpt: "알라모파이어(alamofire) 설치"
  
categories:
  - UIKit
tags:
  - [swift, iOS, alamofire]

permalink: /UIKit/alamofire/ 
toc: true         
toc_sticky: true   
comments: true      
---

# 알라모파이어(alamofire)란 ? 
- Alamofire는 iOS, macOS를 위한 Swift 기반 HTTP 네트워킹 라이브러리입니다.
- 애플에서 자체적으로 네트워크 통신을 위해 제공하는 URLSession API가 있는데, 이를 보완한 것이 Alamofire 입니다.
- Alamofire에서는 다양한 기능을 제공하고 있는데, 자세한 내용은 [Alamofire github 홈페이지](https://github.com/Alamofire/Alamofire)에서 확인가능합니다. 

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

![](/assets/images/categories/uikit/2024-04-02-alamofire1.png)

<br>

## 4. Podfile 더블클릭 
![](/assets/images/categories/uikit/2024-04-02-alamofire2.png)

<br>

## 5. Podfile 내 Alamofire 추가 
![](/assets/images/categories/uikit/2024-04-02-alamofire3.png)

<br>

## 6. Alamofire 설치 
![](/assets/images/categories/uikit/2024-04-02-alamofire4.png)

<br>

## 7.project 재시작 - .xcworkspace 파일을 열어야합니다. 

<br>

## 8. import Alamofire 
- import Alamofire 코드를 추가하고 사용합니다.  

<br>

# 설치 후 에러 발생 시 (snadbox 에러)

![](/assets/images/categories/uikit/2024-04-02-alamofire5.png)

- Update your Xcode project build option `ENABLE_USER_SCRIPT_SANDBOXING` to 'No'.
    - Yes로 되어있어 No로 변경합니다. 

![](/assets/images/categories/uikit/2024-04-02-alamofire6.png)

- 에러 참고 사이트 
    - [https://stackoverflow.com/questions/76590131/error-while-build-ios-app-in-xcode-sandbox-rsync-samba-13105-deny1-file-w](https://stackoverflow.com/questions/76590131/error-while-build-ios-app-in-xcode-sandbox-rsync-samba-13105-deny1-file-w)