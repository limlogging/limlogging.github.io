---
title: "[UIKit] UIScrollView - 화면에서 스크롤 가능한 영역을 제공"
excerpt: "UIScrollView - 화면에서 스크롤 가능한 영역을 제공하는 UI 요소"
  
categories:
  - UIKit
tags:
  - [swift, iOS, UIScrollView]

permalink: /UIKit/UIScrollView/ 
toc: true         
toc_sticky: true   
comments: true      
---

# UIScrollView 
- iOS 애플리케이션에서 스크롤 가능한 컨텐츠를 표시하고 제어하기 위해 사용되는 컨테이너 뷰입니다. 
- UIScrollView는 화면에 표시되는 컨텐츠의 크기가 스크린 크기보다 큰 경우 사용자가 화면을 스크롤하여 컨텐츠를 탐색할 수 있도록 합니다.

## 특징
- 스크롤 가능한 영역 
    - UIScrollView는 보통 자신의 bounds보다 큰 컨텐츠를 포함할 수 있습니다. 사용자는 스크롤하여 이 컨텐츠의 다른 부분을 볼 수 있습니다.
- 스크롤 인디케이터
    - UIScrollView에는 수직 및 수평으로 스크롤 가능한 경우에는 스크롤 인디케이터가 표시됩니다. 이것은 사용자에게 스크롤 가능한 영역의 현재 위치를 시각적으로 보여줍니다.
- 확대 및 축소
    - UIScrollView는 사용자가 핀치(Pinch)하여 확대 또는 축소할 수 있는 확대/축소 동작을 지원합니다.
- 델리게이트 패턴
    - UIScrollView는 UIScrollViewDelegate 프로토콜을 사용하여 사용자 상호 작용 및 스크롤 이벤트를 처리하는 메서드를 호출할 수 있는 델리게이트 패턴을 지원합니다.

## 사용 
- UIScrollView는 많은 다른 뷰와 함께 사용됩니다. 텍스트, 이미지, 뷰, 테이블 뷰 및 컬렉션 뷰와 같은 다양한 컨텐츠를 UIScrollView 내에 배치하여 스크롤 가능한 사용자 인터페이스를 만들 수 있습니다.

# UIScrollView 생성 
```swift
// UIScrollView 생성 및 화면 크기와 같은 프레임 설정
let scrollView = UIScrollView(frame: view.bounds)
```
<br>

# UIScrollView 설정 
## 스크롤 기능을 활성화
```swift
scrollView.isScrollEnabled = true 
```

## 페이지 단위로 스크롤 여부 설정
```swift 
// UIScrollView에서 페이지 단위로 스크롤 여부 설정
scrollView.isPagingEnabled = false 
```

## 스크롤이 끝에 도달할 때 효과 
```swift
// UIScrollView에서 스크롤이 끝에 도달할 때 바운스 효과 활성화
scrollView.bounces = true 
```

## 크기 설정 
```swift
// UIScrollView에 표시되는 전체 컨텐츠의 크기 설정 (가로 스크롤만 가능한 경우 가로 크기만 설정)
scrollView.contentSize = CGSize(width: view.frame.width, height: view.frame.height * 2)
```

## UILabel 생성 및 UIScrollView에 추가
```swift
let label = UILabel(frame: CGRect(x: 0, y: view.frame.height - 30, width: view.frame.width, height: 60))
label.textAlignment = .center
scrollView.addSubview(label)
```
