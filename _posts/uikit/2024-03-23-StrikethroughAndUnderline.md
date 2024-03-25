---
title: "[UIKit] Label 밑줄(underline) 및 가운데줄/취소선(Strikethrough) 긋기"
excerpt: "Label에 밑줄(underline), 취소선(Strikethrough) 긋기"
  
categories:
  - UIKit
tags:
  - [swift, iOS, underline, Strikethrough]

permalink: /UIKit/underlineAndStrikethrough/ 
toc: true         
toc_sticky: true   
comments: true      
---
# NSAttributedString
- 텍스트에 대한 서식 및 스타일을 적용하는 데 사용되는 클래스입니다. 
- NSAttributedString을 사용하면 단순한 문자열을 포맷하고, 텍스트에 다양한 스타일, 폰트, 색상, 그리기 속성 등을 적용할 수 있습니다.
- UILabel, UITextView 및 UITextField와 같은 텍스트 표시 및 입력 컨트롤에서 사용할 수 있습니다. 

# 예제 코드 
- Label을 추가하고 버튼을 선택했을 때 Label에 밑줄 및 취소선이 생기는 예제입니다. 

## 1. Label 및 버튼 추가 
![](/assets/images/categories/uikit/2024-03-23-StrikethroughAndUnderlineMain.png)

## 2. String 확장(extension) 메서드 구현 
```swift
extension String {
    // MARK: - 밑줄
    func underScore() -> NSAttributedString {
        let underScore = NSMutableAttributedString(string: self)        
        // 전체 문자열에 밑줄 스타일 속성을 추가
        underScore.addAttribute(.underlineStyle, value: NSUnderlineStyle.single.rawValue, range: NSMakeRange(0, underScore.length))
        return underScore
    }

    // MARK: - 가운데 밑줄
    func strikeThrough() -> NSAttributedString {
        let attributeString = NSMutableAttributedString(string: self)

        // 전체 문자열에 가운데 밑줄 스타일 속성을 추가
        // NSAttributedString.Key를 사용하여 서식과 속성을 적용할 수 있음(NSAttributedString.Key.strikethroughStyle을 .strikethroughStyle로 사용 가능)
        attributeString.addAttribute(NSAttributedString.Key.strikethroughStyle, value: NSUnderlineStyle.single.rawValue, range: NSMakeRange(0, attributeString.length))        
        return attributeString
    }
}
```

## 3. 밑줄(underline) 버튼 이벤트 
```swift
@IBAction func underLineButtonTapped(_ sender: UIButton) {
    // 레이블의 텍스트에 밑줄을 추가하고 적용
    myLabel.attributedText = myLabel.text?.underScore()
}
```

## 4. 취소선(strikethough) 버튼 이벤트 
```swift
@IBAction func centerLineButtonTapped(_ sender: UIButton) {
    // 레이블의 텍스트에 가운데 밑줄을 추가하고 적용
    myLabel.attributedText = myLabel.text?.strikeThrough()
}
```

## 5. 실행 확인 
- 밑줄(underline)
![](/assets/images/categories/uikit/2024-03-23-Underline.png)

- 취소선(strikethough)
![](/assets/images/categories/uikit/2024-03-23-Strikethrough.png)

# 마무리 
- NSAttributedString을 사용하면 다양한 스타일을 적용하여 텍스트를 꾸미는 데 유용하다. 
- NSAttributedString은 한 번 생성되면 수정할 수 없음. 텍스트를 수정하려면 새로운 NSAttributedString을 생성해야함.