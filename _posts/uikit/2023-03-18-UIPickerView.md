---
title: "[UIKit] UIPickerView - 회전 가능한 휠 형식"
excerpt: "UIPickerView - 사용자가 여러 개의 옵션 중 하나를 선택할 수 있는 회전 가능한 휠 형식의 UI 요소"
  
categories:
  - UIKit
tags:
  - [swift, iOS, UIPickerView]

permalink: /UIKit/UIPickerView/ 
toc: true         
toc_sticky: true   
comments: true      
---

# UIPickerView 
- iOS 애플리케이션에서 선택지를 제공하고 사용자가 그 중 하나를 선택할 수 있도록 하는 뷰입니다. 
- 주로 특정한 선택지를 제공하고 사용자가 그 중 하나를 선택할 때 사용됩니다.

## 특징
- 선택지 표시
    - UIPickerView는 여러 개의 컴포넌트를 가질 수 있으며, 각 컴포넌트에는 여러 개의 행(row)이 포함될 수 있습니다. 각 행은 하나의 선택지를 나타냅니다.
- 스크롤 기능
    - 사용자는 UIPickerView의 컴포넌트를 위아래로 스크롤하여 여러 선택지 중 원하는 항목을 찾을 수 있습니다.
- 델리게이트 및 데이터 소스
    - UIPickerView는 데이터와 상호 작용하기 위해 데이터 소스 및 델리게이트 패턴을 사용합니다. 데이터 소스는 UIPickerView에 대해 표시할 데이터를 제공하고, 델리게이트는 사용자 상호 작용 및 선택 이벤트를 처리합니다.

## 사용 
- UIPickerView는 주로 날짜, 시간, 지역, 선택 리스트, 옵션 등과 같이 여러 선택지 중에서 하나를 선택할 필요가 있는 경우에 사용됩니다.

# 주요 속성
## dataSource 
- UIPickerView의 데이터를 제공하는 객체를 설정합니다. 

## delegate 
- UIPickerView의 이벤트를 처리하는 객체를 설정합니다. 

## numberOfComponents 
- UIPickerView에서 표시할 구성 요소의 수를 반환합니다. 

## selectedRow(inComponent:)
- 지정된 구성 요소에서 선택된 행의 인덱스를 반환합니다. 

# UIScrollView 설정 
## 예제 코드
```swift
import UIKit
class ViewController: UIViewController, UIPickerViewDelegate, UIPickerViewDataSource {
    let pickerView = UIPickerView()
    let data = ["Apple", "Banana", "Orange", "Grape", "Pineapple"]

    override func viewDidLoad() {
        super.viewDidLoad() 

        //UIPickerView의 delegate 및 dataSource를 ViewController로 설정
        pickerView.delegate = self
        pickerView.dataSource = self
        
        //pickerView를 화면의 중앙에 위치
        pickerView.center = view.center 
        
        //pickerView를 ViewController의 뷰에 추가
        view.addSubview(pickerView)
    }

    //UIPickerViewDataSource 프로토콜의 필수 메서드로, UIPickerView에 표시할 컴포넌트(열)의 개수를 반환
    func numberOfComponents (in pickerView: UIPickerView) -> Int {
        return 1
    }

    //UIPickerViewDataSource 프로토콜의 필수 메서드로, 각 컴포넌트(열)에 표시할 행의 개수를 반환
    func pickerView(_ pickerView: UIPickerView, numberOfRowsInComponent component: Int) -> Int {
        return data.count
    }

    //UIPickerViewDelegate 프로토콜의 선택적 메서드로 사용자가 특정 행을 선택 했을때 호출 
    func pickerView(_ pickerView: UIPickerView, titleForRow row: Int, forComponent component: Int) -> String? {
        return data[row]
    }

    //선택된 과일을 출력 
    func pickerView(_ pickerView: UIPickerView, didSelectRow row: Int, inComponent component: Int) {
        print("Selected: \(data[row])")
    }
}
```
