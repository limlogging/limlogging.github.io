---
title: "[UIKit] UITableView - 데이터 목록 표시"
excerpt: "UITableView - 데이터 목록을 표시하고 사용자와 상호 작용할 수 있는 스크롤 가능한 UI 요소"
  
categories:
  - UIKit
tags:
  - [swift, iOS, UITableView]

permalink: /UIKit/UITableView/ 
toc: true         
toc_sticky: true   
comments: true      
---

# UITableView 
- iOS 애플리케이션에서 테이블 형식의 데이터를 표시하고 관리하는 데 사용되는 중요한 뷰 컴포넌트입니다. 
- 테이블 뷰는 여러 행으로 구성되며, 각 행에는 하나 이상의 셀이 포함됩니다. 
- 각 셀은 사용자 인터페이스에 정보를 표시하거나 사용자 상호 작용을 위한 컨트롤을 제공합니다.

## 특징
- 다양한 셀 유형
    - UITableView는 특정 유형의 데이터를 표시하기 위해 다양한 스타일과 레이아웃의 셀을 지원합니다. 텍스트, 이미지, 버튼 등 다양한 컨텐츠를 포함할 수 있습니다.
- 스크롤 기능
    - 테이블 뷰는 데이터가 많거나 너무 긴 경우에도 스크롤하여 모든 데이터에 접근할 수 있도록 합니다.
- 섹션 및 인덱스
    - UITableView는 섹션을 사용하여 데이터를 구성하고 섹션 인덱스를 제공하여 사용자가 특정 부분으로 빠르게 이동할 수 있도록 합니다.
- 셀 재사용
    - UITableView는 셀을 효율적으로 관리하기 위해 셀 재사용 메커니즘을 사용합니다. 이는 메모리 사용량을 최적화하고 성능을 향상시킵니다.
- 델리게이트 및 데이터 소스
    - UITableView는 UITableViewDelegate 및 UITableViewDataSource 프로토콜을 사용하여 사용자 상호 작용 및 데이터 관리를 처리합니다. 데이터 소스는 UITableView에 표시할 데이터를 제공하고, 델리게이트는 사용자 상호 작용 및 테이블 뷰의 동작을 제어합니다.

## 사용 
- iOS 애플리케이션에서 매우 일반적으로 사용됩니다. 
- 메시지 리스트, 설정 화면, 사용자 목록 등

# 주요 속성 
## dataSource 
- UITableView의 데이터를 제공하는 객체를 설정합니다. 

## delegate 
- UITableView의 이벤트를 처리하는 객체를 설정합니다. 

## rowHeight 
- 각 행의 높이를 설정합니다.

## separatorStyle
- 행 간 구분선의 스타일을 설정합니다. 

## separatorColor
- 행 간 구분선의 색상을 설정합니다. 

## allowsSelection 
- 테이블 뷰에서 행 선택을 허용할지 여부를 설정합니다. 

# UITableView 설정 
## 예제 코드
```swift
import UIKit
  
class ViewController: UIViewController, UITableViewDataSource, UITableViewDelegate {  
      
    let tableView = UITableView()  
    let data = ["Item 1", "Item 2", "Item 3"]  
      
    override func viewDidLoad() {  
        super.viewDidLoad()  
        //tableView의 프레임을 현재 뷰의 경계에 맞게 설정
        tableView.frame = view.bounds  
        
        //UITableView의 데이터 소스 및 델리게이트를 ViewController로 설정
        tableView.dataSource = self  
        tableView.delegate = self  

        tableView.register(UITableViewCell.self, forCellReuseIdentifier: "Cell")  
        view.addSubview(tableView)  
    }  
      
    // UITableViewDataSource		
    /* [필수] 테이블의 행 수를 보고합니다. */
    // section: 테이블뷰의 section을 나타내는 식별자 입니다. 이를 바탕으로 해당 섹션의 count를 반환합니다.
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {  
        return data.count  
    }  
    
    /* [필수] 테이블의 각 행에 대한 셀을 제공합니다. */
    // indexPath: 테이블뷰에서 Row(행)을 찾는 경로입니다. 이를 바탕으로 적절한 cell을 반환합니다.
    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {  
        let cell = tableView.dequeueReusableCell(withIdentifier: "Cell", for: indexPath)  
        cell.textLabel?.text = data[indexPath.row]  
        return cell  
    }  
      
    // UITableViewDelegate	
    /* 행이 선택되었을 때 호출 */
    // indexPath: 테이블뷰에서 선택된 Row(행)을 찾는 경로입니다. 이를 바탕으로 어떤 행이 선택되었는지 파악할 수 있습니다.
    func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {  
        print("Selected: \(data[indexPath.row])")  
        tableView.deselectRow(at: indexPath, animated: true)  
    }  
}
```
