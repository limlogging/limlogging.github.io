---
title: "[UIKit] UITextField - 사용자에게 텍스트 입력 받기"
excerpt: "UITextField - 사용자로부터 텍스트를 입력받는 데 사용"
  
categories:
  - UIKit
tags:
  - [swift, iOS, UITextField]

permalink: /UIKit/UITextField/ 
toc: true         
toc_sticky: true   
comments: true      
---

# UITextField 
- UITextField는 UIKit 프레임워크에서 제공하는 클래스 중 하나로, 사용자로부터 텍스트를 입력받는 데 사용
- 텍스트 필드, 검색 상자 또는 비밀번호 필드 등을 생성할 때 사용

# UITextField 생성 
```swift
let textField = UITextField() 
```
<br>

# UITextField 설정 
## 입력 유도 메시지 
```swift
textField.placeholder = "텍스트를 입력하세요."
```

## UITextField 모양 
```swift
//둥근 테두리 
textField.borderStyle = .roundedRect
```

## 입력용 키보드 설정 
- 사용자가 해당 입력 필드에 입력할 때 사용할 키보드의 종류를 지정

```swift
//일반 텍스트 입력용 키보드
textField.keyboardType = .default
//이메일 주소 입력 
textField.keyboardType = .emailAddress
//숫자만 입력 
textField.keyboardType = .numberPad

/* 입력용 키보드 종류 
Default: 일반적인 키보드로, 텍스트 및 숫자를 입력할 수 있습니다.
ASCIICapable: ASCII 문자만 입력할 수 있는 키보드입니다.
Numbers and Punctuation: 숫자와 일부 구두점 기호를 입력할 수 있는 키보드입니다.
URL: URL 입력에 특화된 키보드로, .com 버튼이나 / 버튼이 추가되어 있습니다.
NumberPad: 숫자만 입력할 수 있는 패드 형태의 키보드입니다.
PhonePad: 전화번호를 입력할 때 사용하는 패드 형태의 키보드입니다.
DecimalPad: 십진수를 입력할 수 있는 숫자 패드입니다. 소수점을 사용할 수 있습니다.
EmailAddress: 이메일 주소를 입력하는데 특화된 키보드입니다.
Twitter: 트위터 관련 기호와 사용할 수 있는 키보드입니다.
WebSearch: 웹 검색에 사용할 수 있는 키보드입니다.
*/
```

## 보안 입력(비밀번호 등) 
```swift
//일반 텍스트 입력용 키보드
textField.isSecureTextEntry = false
```

## 리턴(엔터) 키의 종류
```swift
//일반 텍스트 입력용 키보드
textField.returnKeyType = .done

/* ReturnKeyType의 종류
default: 기본 동작으로, 텍스트 필드의 입력을 완료합니다.
go: "이동"이라는 동작을 수행합니다. 주로 키보드의 Return 키가 "이동" 동작을 수행하는데 사용됩니다. 예를 들어, 로그인 화면에서 사용자가 아이디와 비밀번호를 입력한 후 Return 키를 누르면 비밀번호 입력 필드로 이동할 때 사용됩니다.
google: "Google" 동작을 수행합니다. 일반적으로 웹 검색 화면에서 사용됩니다.
join: "가입" 동작을 수행합니다. 주로 가입 양식에서 사용됩니다.
next: "다음" 동작을 수행합니다. 주로 다음 입력 필드로 포커스를 이동할 때 사용됩니다.
route: "경로" 동작을 수행합니다. 예를 들어, 지도 앱에서 사용될 수 있습니다.
search: "검색" 동작을 수행합니다. 주로 검색 창에서 사용됩니다.
send: "전송" 동작을 수행합니다. 주로 메시지를 전송하는 화면에서 사용됩니다.
done: "완료" 동작을 수행합니다. 편집 모드를 종료하거나 텍스트 입력을 완료하는 데 사용됩니다.
emergencyCall: "긴급 전화" 동작을 수행합니다. 긴급 전화를 걸거나 전화 앱을 실행하는 데 사용됩니다.
*/
```