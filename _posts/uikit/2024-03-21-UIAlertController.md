---
title: "[UIKit] 얼러트 컨트롤러(UIAlertController) "
excerpt: "UIAlertController - 경고 메시지, 알림 창, 사용자 선택 옵션 팝업 창 제공"
  
categories:
  - UIKit
tags:
  - [swift, iOS, UIAlertController]

permalink: /UIKit/UIAlertController/ 
toc: true         
toc_sticky: true   
comments: true      
---

# 얼러트 컨트롤러(UIAlertController)란? 
- iOS 애플리케이션에서 경고 메시지, 알림 창, 또는 사용자에게 선택 옵션을 제공하는 팝업 창을 표시하는 데 사용되는 클래스입니다. 
- UIKit 프레임워크에서 제공되며, 모든 iOS 버전에서 사용할 수 있습니다.

# 스타일 
- .alert (경고 메시지 / 알림) 
- .actionSheet (사용자 선택 옵션 목록)

# 예제 코드 
## 1. 버튼 추가 
- 버튼을 선택했을 때 Alert 창을 띄우기 위해서 버튼을 추가합니다. 
- "alert 테스트" 버튼을 추가했습니다.
![](/assets/images/categories/uikit/2024-03-21-alertTestButton.png)

## 2. UIAlertController 생성 
```swift
@IBAction func alertTestButtonTapped(_ sender: UIButton) {
    //제목은 할일 추가로, 메시지는 할일을 추가하세요로 표시
    let alertController = UIAlertController(title: "할일 추가", message: "할일을 추가하세요", preferredStyle: .alert)
}
```

## 3. UIAlertController를 화면에 표시 (present)
```swift
@IBAction func alertTestButtonTapped(_ sender: UIButton) {
    let alertController = UIAlertController(title: "할 일 추가", message: "할 일을 추가하세요", preferredStyle: .alert)

    //present 메서드를 사용하여 화면에 모달로 표시, 추가하지 않으면 안보임
    self.present(alertController, animated: true, completion: nil)
}
```

## 4. alert 동작 확인
- preferredStyle에 따라서 스타일이 달라집니다. 

|preferredStyle: .alert|preferredStyle: .actionSheet|
|:---:|:---:|
|<img src="/assets/images/categories/uikit/2024-03-21-preferredStyleAlert.png">|<img src="/assets/images/categories/uikit/2024-03-21-preferredStyleActionSheet.png">|

## 5. alert에 취소 버튼 추가
- alert 창에서 버튼이 없어서 창을 닫을 수가 없습니다. 
- 취소 버튼을 추가합니다. 
```swift
@IBAction func alertTestButtonTapped(_ sender: UIButton) {
    let alertController = UIAlertController(title: "할 일 추가", message: "할 일을 추가하세요", preferredStyle: .alert)

    // "취소" 버튼을 생성합니다. 제목은 "취소"로, 스타일은 .cancel로 설정합니다.        
    let cancelButton = UIAlertAction(title: "취소", style: .cancel, handler: nil)
    //생성한 "취소" 버튼을 UIAlertController에 추가합니다.
    alertController.addAction(cancelButton)
    
    self.present(alertController, animated: true, completion: nil)
}
```
- 취소 버튼이 생기고 취소가 가능해졌습니다. 
![](/assets/images/categories/uikit/2024-03-21-alertCancelButton.png)

## 6. alert에 TextField 추가 
- UIAlertController의 addTextField를 사용하여 TextField를 추가합니다.  
```swift
alertController.addTextField { textField in
    textField.placeholder = "할 일을 입력하세요."
}
```
- 텍스트 필드를 확인 할 수 있습니다. 
![](/assets/images/categories/uikit/2024-03-21-alertTextField.png)

## 7. TextField를 처리할 추가 버튼 생성 
- 취소 버튼 추가할때와 방법이 같습니다. 
```swift        
let addButton = UIAlertAction(title: "추가", style: .default) 
alertController.addAction(addButton)                
```
- 실행해보면 버튼은 추가 됐는데 입력값을 처리할 수 없습니다. 
- 입력 값 확인을 위해 코드를 수정합니다. 
```swift        
let addButton = UIAlertAction(title: "추가", style: .default) { _ in
    // 사용자가 입력한 값을 확인하고 처리합니다.
    if let textField = alertController.textFields?.first, let text = textField.text {
        print("입력된 값: \(text)")
    }
}
alertController.addAction(addButton)          
```
- 값 입력 
![](/assets/images/categories/uikit/2024-03-21-alertTextFieldInputValue.png)
- 출력 결과 확인
![](/assets/images/categories/uikit/2024-03-21-result.png)

# 마무리 
- UIAlertController를 사용하면 delegate를 사용하지 않고도 사용자의 상호작용을 처리할 수 있다 !!! 