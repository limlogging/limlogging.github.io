---
title: "[UIKit] UIImageView - 이미지 표시"
excerpt: "UIImageView - 이미지를 표시하는 데 사용되는 UI 요소"
  
categories:
  - UIKit
tags:
  - [swift, iOS, UIImageView]

permalink: /UIKit/UIImageView/ 
toc: true         
toc_sticky: true   
comments: true      
---

# UIImageView 
- UIKit 프레임워크에서 제공하는 클래스로, 이미지를 표시하는 데 사용

# UIImageView 생성 
```swift
let imageView = UIImageView() 
```
<br>

# UIImageView 설정 
## 표시할 이미지 설정
```swift
//이미지 파일명으로 UIImage 객체 생성 
let image = UIImage(named: "exampleImage")
imageView.image = image  
```

## UIImageView 위치와 크기를 정의 
```swift
//화면에서 (x: 50, y: 100)에 위치하고, 너비가 200포인트이고 높이가 150포인트인 사각형 영역에 해당하는 위치에 표시
imageView.frame = CGRect(x: 50, y: 100, width: 200, height: 150) 
```

## image 표시할때 contentMode 설정 
- 이미지 뷰의 크기와 이미지의 크기가 다를 때 .scaleAspectFit 모드를 사용하면 이미지가 이미지 뷰에 적절히 맞춰져서 화면에 나타남

```swift
//scaleAspectFit모드는 이미지의 비율을 유지하면서 이미지가 이미지 뷰에 딱 맞도록 확대 또는 축소되어 표시
imageView.contentMode = .scaleAspectFit
```