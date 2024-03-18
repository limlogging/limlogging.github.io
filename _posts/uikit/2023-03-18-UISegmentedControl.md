---
title: "[UIKit] UISegmentedControl - 세그먼트를 선택하여 원하는 옵션을 선택"
excerpt: "UISegmentedControl - 여러개의 세그먼트로 구성된 컨트롤로 각 세그먼트를 선택하여 원하는 옵션을 선택할 수 있는 UI 요소"
  
categories:
  - UIKit
tags:
  - [swift, iOS, UISegmentedControl]

permalink: /UIKit/UISegmentedControl/ 
toc: true         
toc_sticky: true   
comments: true      
---

# UISegmentedControl 
- iOS 앱에서 여러 개의 상호 배타적인 옵션 중 하나를 선택할 수 있는 컨트롤입니다. 
- 사용자는 UISegmentedControl을 탭하여 여러 세그먼트 중 하나를 선택할 수 있습니다. 각 세그먼트는 다른 옵션을 나타내며, 사용자는 이를 탭하여 해당 옵션을 선택합니다.

## 특징
- 상호 배타적인 선택
    - 여러 옵션 중 하나만 선택할 수 있습니다. 한 번에 한 옵션만 선택됩니다.
- 시각적 표시
    - 각 세그먼트는 사용자에게 다른 옵션을 시각적으로 표시합니다.
- 값 변경 이벤트
    - 사용자가 세그먼트를 선택할 때마다 값을 변경하는 이벤트가 발생합니다.

## 사용 
1. 여러 가지 옵션 중 하나를 선택해야 하는 경우 (예: 탭 스타일 탐색 메뉴)
2. 서로 다른 뷰 또는 데이터를 전환해야 하는 경우 (예: 세그먼트 컨트롤을 사용하여 다른 보기를 전환하는 탭 컨트롤러)

# 세그먼트(Segment)란?
- 세그먼트(Segment)란 일정한 단위로 분할된 부분

# UISegmentedControl 생성 
```swift
let items = ["Option 1", "Option 2", "Option 3"]
let segmentedControl = UISegmentedControl(items: items)
```
<br>

# UISegmentedControl 설정 
## 초기 선택된 세그먼트 인덱스 설정 
```swift
segmentedControl.selectedSegmentIndex = 0 //초기 선택된 세그먼트 인덱스 설정 
```

## 세그먼트 컨트롤 색상 설정 
```swift 
segmentedControl.tintColor = UIColor.blue 
```

## 선택 표시를 유지할지 여부 설정 
```swift
segmentedControl.isMomentary = false 
```

## 세그먼트 값 변경 이벤트 처리 
```swift
segmentedControl.addTarget(self, action: #selector(segmentValueChanged(_:)), for: .valueChanged)
/*
첫 번째 매개변수 self는 이벤트를 수신할 대상을 나타냅니다. 일반적으로는 현재의 뷰 컨트롤러를 가리킵니다.
두 번째 매개변수 action은 이벤트가 발생했을때 호출될 메서드, @objc 어노테이션이 붙어있어야함. 
- #selector는 Objective-C에서 메서드를 식별하는 문법 
- @objc는 Swift 코드와 Objective-C와 상호작용하게 해줌
세 번째 매개변수 for는 이벤트 처리기 선택, valueChange는 버튼이 눌렀을때 호출 
*/
/* .valueChange에 들어갈 수 있는 이벤트 
.touchDown: 사용자가 스위치를 터치할 때 호출됩니다.
.touchDownRepeat: 사용자가 스위치를 연속해서 터치할 때 호출됩니다.
.touchDragInside: 사용자가 스위치를 내부로 드래그할 때 호출됩니다.
.touchDragOutside: 사용자가 스위치를 외부로 드래그할 때 호출됩니다.
.touchDragEnter: 사용자가 스위치의 영역으로 드래그할 때 호출됩니다.
.touchDragExit: 사용자가 스위치의 영역을 벗어날 때 호출됩니다.
.touchUpInside: 사용자가 스위치를 터치하고 놓을 때 호출됩니다. (가장 흔히 사용됨)
.touchUpOutside: 사용자가 스위치 외부에서 터치하고 놓을 때 호출됩니다.
.valueChanged: 스위치의 값이 변경될 때 호출됩니다. (가장 흔히 사용됨)
.primaryActionTriggered: 주요 작업이 트리거될 때 호출됩니다. (예: 터치를 누를 때)
.editingDidBegin: 편집이 시작될 때 호출됩니다. (예: 텍스트 필드 편집이 시작될 때)
.editingChanged: 편집 내용이 변경될 때 호출됩니다. (예: 텍스트 필드의 텍스트가 변경될 때)
.editingDidEnd: 편집이 종료될 때 호출됩니다. (예: 텍스트 필드 편집이 종료될 때)
*/

@objc func segmentValueChange(_ sender: UISegmentedControl) {
    print("Selected segment index: \(sender.selectedSegmentIndex)")
}
```
