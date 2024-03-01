---
title: "[내배캠] 온보딩 주차 프로젝트 만들기"
excerpt: "짧은 기간(4일)에 간단한 앱 만들기 프로젝트 진행하였습니다. (진짜 간단)"
categories: sparta
tags: [mini Project]

permalink: /sparta/firstProject/ #md 파일 제목과 다르게 url을 지정할 수 있음, 미지정 시 md 파일 명으로 따라감   
toc: true         #On this page 보이기 
toc_sticky: true  #on this page 스크롤에 따라 움직이도록 
---
# 프로젝트 
1. 프로젝트 주제: 팀 소개 앱 만들기 
2. 프로젝트 기간: 2/26(월) ~ 2/29(목)  
3. 인원: 4명 (팀장: 김건응 / 팀원: 박중권, 서수영, 임형섭)   
4. 주요 기능: 팀원명 선택 시 해당 팀원 정보 확인 가능 

<br>

# 프로젝트 진행 프로세스 
1. 사다리 타기를 통해 팀장 선정 
<br>네이버 사다리를 통해 김건응님 팀장 선정  
2. 개발 전 프로그램 디자인 하기
<br>종이에 그리기, figma 웹, 스토리보드에 그리기 등   
3. 다수결에 의한 디자인 선정  
figma로 작성하신 김건응 팀장님 디자인으로 진행하기로 하였습니다. 
![](/assets/images/categories/sparta/firstProjectDesign.png)
4. 선출된 디자인을 각자 구현 (매일 저녁 진행 단계 확인)
5. 다수결에 의한 결과물 선정 

<br>

# 역할 분담 
## 김건응 
1. 스토리보드 기반 컬렉션뷰를 사용한 하단 바를 구현하려 했고, 각 팀원의 이름과 사진을 버튼으로 만들어 클릭 시 해당 프로필과 소개가 나오는 기능을 구현하려 하였습니다.
![](/assets/images/categories/sparta/firstProjectKim1.png)

## 박중권
1. Button (홈, 김건응, 임형섭, 서수영, 박중권, More)
Button을 눌렀을 때, 홈은 홈 화면으로, 맴버들 이름을 눌렀을 땐 각 맴버의 소개 페이지로 이동할 수 있는 버튼을 만들었습니다.
![](/assets/images/categories/sparta/firstProjectPark1.png)
2. UIView 음영
기본 UIView가 View와 배경색이 같은 경우, 경계를 알 수 있게 음영을 추가해서 이펙트를 넣었습니다.
![](/assets/images/categories/sparta/firstProjectPark2.png)
3. 원형 Button 
스토리보드를 통해서 Button의 모양을 바꾸는데 있어서 제한적인 부분이 많아, 구글링을 한 후 Button의 모양을 코드를 사용해 변경했습니다.
![](/assets/images/categories/sparta/firstProjectPark3_1.png)
버튼을 둥글게 하기 위해 
```swift
self.RoundButton1.layer.masksToBounds = true 
self.RoundButton1.layer.masksToBounds = self.RoundButton1.frame.size.width / 2 
```
코드를 사용하여 아래와 같이 구현하였습니다. 
![](/assets/images/categories/sparta/firstProjectPark3_2.png)
4. Image 추가
Asset에 Image를 추가 후, 삽입.

## 서수영 
1. 코드베이스로 컬렉션 뷰 구현, 스택 뷰 레이아웃 설정, 컬렉션 뷰 터치 이벤트를 구현하려고 하였습니다. 
![](/assets/images/categories/sparta/firstProjectseo1.png)

## 임형섭 
1. xcode에 포함된 스포이드를 사용하여 선정된 디자인과 동일한 색상 및 디자인을 구현하였습니다. 
![](/assets/images/categories/sparta/firstProjectlim1.png)
2. 팀원들의 제안을 받아 Scroll View, Table View를 추가하였습니다. 
![](/assets/images/categories/sparta/firstProject5.png)
3. 다양한 기능보다 우선 완성할 수 있도록 진행하였습니다.  

<br>

# 어려웠던 점 
* 실제로 그린 디자인을 구현하려면 어떤 button, controller 등을 사용해야하는지 몰라 어려웠습니다. 

<br>

# 해결한 내용 
1. Scroll View에서 inspectors에서 추가적인 설정을 통한 Scroll 기능 구현 
2. button 5개의 이벤트를 1개의 함수로 구현하였습니다.  
3. 구조체를 사용하여 팀원 정보 인스턴스를 생성하였습니다.  
4. Table View, Table View Cell 사용 시 필수로 사용해야하는 함수를 확인하여 구현하였습니다. 

<br>

# 해결하지 못한 내용 
TableView에서 데이터를 표출하고 다음 view로 이동하는것에 어려움이 있었습니다.  
Tab Bar, Navigation Controller는 사용하지 못했습니다. 

<br>

# 최종 결과물 
![](/assets/images/categories/sparta/firstProject1.png)
![](/assets/images/categories/sparta/firstProject2.png)
![](/assets/images/categories/sparta/firstProject3.png)
![](/assets/images/categories/sparta/firstProject4.png)
![](/assets/images/categories/sparta/firstProject5.png)

<br>

# 느낀 점
짧은 기간이지만 기본적인 Button, Lable 사용, 사진 넣기, 단축키 등 조금 익숙해 질 수 있었습니다.  
또한 실제 디자인과 구현은 차이가 있다는 걸 알았습니다. 