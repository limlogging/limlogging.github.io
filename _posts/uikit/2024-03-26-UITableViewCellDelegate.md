---
title: "[UIKit] Tableview Cell에서 Delegate 사용"
excerpt: "Cell Class와 View Class와 상호작용 "
  
categories:
  - UIKit
tags:
  - [swift, iOS, Tableview Cell Delegate]

permalink: /UIKit/UITableViewCellDelegate/ 
toc: true         
toc_sticky: true   
comments: true      
---

# TableViewCell과 ViewController와 상호작용
- TableViewCell에는 ViewController에서 가져온 데이터를 보여줍니다. 
- Cell에서 스위치의 데이터를 변경하고 새로운 데이터를 추가하면 switch 정보가 초기화가 됩니다. 
- Cell에서 스위치를 변경할때 ViewController의 배열의 값도 변경하면 새로운 값이 추가되어도 스위치의 Value가 바뀌지 않을 것 입니다.
<video width="640" height="360" controls>
    <source src="../../assets/video/2024-03-26-UITableViewCellDelegate1.mov" type="video/mp4">
</video>

# 예제 코드 
- Cell에서 스위치를 변경할때 ViewController의 배열의 값도 변경하면 새로운 값이 추가되어도 스위치의 Value가 바뀌지 않도록하는 예제입니다. 

## 1. 스위치 ValueChanged 액션함수 생성 
```swift
// MARK: - 스위치 변경 이벤트
@IBAction func switchValueChanged(_ sender: UISwitch) {
}
```

## 2. 스위치 Delegate 프로토콜 정의 
- 스위치 값이 변경될때마다 해당 정보를 View Controller로 전달 할 수 있는 프로토콜을 Cell class에 정의합니다.

```swift
import UIKit

//스위치 값이 변경될때마다 해당 정보를 View Controller로 전달 할 수 있는 프로토콜을 정의
protocol MyToDoListCellDelegate: AnyObject {
    func switchValueChanged(_ cell: MyToDoListCell, isOn: Bool) // 스위치 값 변경 시 호출할 메서드
}

class MyToDoListCell: UITableViewCell {
``` 

## 3. 스위치 Delegate 선언 
```swift
// 스위치 값 변경 이벤트를 처리할 delegate를 선언합니다.
var delegate: MyToDoListCellDelegate?   // 스위치 값 변경 이벤트를 처리할 delegate

override func awakeFromNib() {
    super.awakeFromNib()
}
``` 

## 4. 스위치 ValueChanged 액션함수 수정 
```swift
// MARK: - 스위치 변경 이벤트
@IBAction func switchValueChanged(_ sender: UISwitch) {
    // delegate를 통해 스위치 값 변경 이벤트를 처리할 메서드를 호출합니다.
    delegate?.switchValueChanged(self, isOn: sender.isOn)
}
```

## 5. ViewController에서 스위치 델리게이트 채택 
- ViewController를 확장하여 스위치 델리게이트 채택 

```swift
// MARK: - 스위치 변경 이벤트 처리를 위한 Delegate 채택
extension ViewController: MyToDoListCellDelegate {
    //필수메서드를 구현하라고 에러가 발생하고 에러를 선택하면 Cell 클래스에서 만들어 놓은 함수가 만들어진다. 
    func switchValueChanged(_ cell: MyToDoListCell, isOn: Bool) {
          <#code#>
    }
}
```

## 6. Cell의 인덱스를 구하고 스위치 Bool 값을 배열에 반영
```swift
// MARK: - 스위치 변경 이벤트 처리를 위한 Delegate 채택
extension ViewController: MyToDoListCellDelegate {
  //필수메서드를 구현하라고 에러가 발생하고 에러를 선택하면 Cell 클래스에서 만들어 놓은 함수가 만들어진다. 
  func switchValueChanged(_ cell: MyToDoListCell, isOn: Bool) {
    //해당 셀의 인덱스 가져오기
    guard let indexPath = myTodoListTableView.indexPath(for: cell) else {
      return
    }
    // 스위치 값을 배열에 반영
    //ViewController에 선언한 myToDoListArray 배열에 변경된 스위치 값 설정  
    myToDoListArray[indexPath.row].toDoIsComplete = isOn
  }
}
```

## 7. ⭐️⭐️⭐️ 스위치 값 변경 이벤트 처리를 위한 Delegate 설정 
- cellForRowAt 함수 리턴 부분 위에 cell.delegate = self를 추가합니다. 
- 셀에서 발생한 이벤트를 뷰 컨트롤러에서 처리할 수 있도록 연결합니다. 

```swift
// MARK: - TableView Row에서 보여줄 컨텐츠
func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
    //다른코드 생략 
    cell.delegate = self    //스위치 값 변경 이벤트 처리를 위한 delegate 설정
    return cell
} 
```

## 8. 실행화면
- 스위치 변경 시 배열의 값도 변경하여 데이터를 추가해도 스위치가 초기화되지 않습니다. 
<video width="640" height="360" controls>
    <source src="../../assets/video/2024-03-26-UITableViewCellDelegate2.mov" type="video/mp4">
</video>

# 스위치 토글 시 취소선(strikeThrough) 추가
## 1. String 확장 메서드 구현 
- [참고: [UIKit] Label 밑줄(underline) 및 가운데줄/취소선(Strikethrough) 긋기](https://limlogging.github.io/UIKit/underlineAndStrikethrough/){:target="_blank"}

```swift
// MARK: - String 확장(extension) 메서드에 취소선 구현
extension String {
    func strikeThrough() -> NSAttributedString {
        // NSAttributedString.Key를 사용하여 서식과 속성을 적용할 수 있음(NSAttributedString.Key.strikethroughStyle을 .strikethroughStyle로 사용 가능)
        let attributeString = NSMutableAttributedString(string: self)
        // 전체 문자열에 취소선 스타일 속성을 추가
        attributeString.addAttribute(NSAttributedString.Key.strikethroughStyle, value: NSUnderlineStyle.single.rawValue, range: NSMakeRange(0, attributeString.length))
        return attributeString
    }
}
```

## 2. cellForRowAt 메서드 수정
- switch 값에 따른 취소선 적용 및 취소선 취소 

```swift
    // MARK: - TableView Row에서 보여줄 컨텐츠
    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        // 다른코드 생략 

        //title 취소선 - switch 값에 따라 취소선 또는 일반 Text
        if cell.myToDoIsCompleteSwitch.isOn {
            // 해당 텍스트에 취소선을 적용한 NSAttributedString을 생성
            let attributedText = myToDoListArray[indexPath.row].toDoTitle.strikeThrough()
            // 취소선이 적용된 NSAttributedString을 텍스트로 설정
            cell.myToDoTitleLabel.attributedText = attributedText
        } else {
            //일반 Text - 취소선 없애기
            cell.myToDoTitleLabel.attributedText = NSAttributedString(string: myToDoListArray[indexPath.row].toDoTitle)
        }

        cell.delegate = self    //스위치 값 변경 이벤트 처리를 위한 delegate 설정
        return cell
    }
```

## 3. Cell 새로고침 추가 
- 스위치 변경 후 label에 취소선을 적용시키도록 새로고침 추가 
- myTodoListTableView.reloadRows(at: [indexPath], with: .automatic)

```swift
// MARK: - 스위치 변경 이벤트 처리를 위한 Delegate 채택
extension ViewController: MyToDoListCellDelegate {
    func switchValueChanged(_ cell: MyToDoListCell, isOn: Bool) {
        //해당 셀의 인덱스 가져여오기
        guard let indexPath = myTodoListTableView.indexPath(for: cell) else {
            return
        }        
        // 스위치 값을 배열에 반영
        myToDoListArray[indexPath.row].toDoIsComplete = isOn
        // 스위치가 변경될 때마다 테이블 뷰의 해당 셀만 다시 로드, 취소선 때문에
        myTodoListTableView.reloadRows(at: [indexPath], with: .automatic)
    }
}
```
## 4. 실행화면 
<video width="640" height="360" controls>
    <source src="../../assets/video/2024-03-26-UITableViewCellDelegate3.mov" type="video/mp4">
</video>

# 마무리 
- 데이터를 주는 곳에서 델리게이트를 만들고 데이터를 받는 곳에서 델리게이터를 채택하고 사용 
  1. Cell클래스의 @IBAction func switchValueChanged(_ sender: UISwitch) 함수 먼저 실행 
  2. View클래스에서 델리게이트 채택 후 switchValueChanged 함수에서 스위치 변경 이벤트 처리 