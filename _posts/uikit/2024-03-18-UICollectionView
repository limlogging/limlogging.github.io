---
title: "[UIKit] UICollectionView - 그리드나 리스트 표시"
excerpt: "UICollectionView - 유연한 그리드 레이아웃을 사용하여 아이템 목록을 표시하고 사용자와 상호 작용할 수 있는 스크롤 가능한 UI 요소"
  
categories:
  - UIKit
tags:
  - [swift, iOS, UICollectionView]

permalink: /UIKit/UICollectionView/ 
toc: true         
toc_sticky: true   
comments: true      
---

# UICollectionView 
-  iOS 애플리케이션에서 그리드나 리스트 형식으로 데이터를 표시하는 데 사용되는 유연한 레이아웃을 가진 뷰입니다. 
- UICollectionView는 UITableView와 유사하지만, 보다 다양한 레이아웃과 사용자 정의 가능한 셀 디자인을 제공합니다.

## 특징
- 다양한 레이아웃
    - UICollectionView는 그리드, 리스트, 덱스(Stack), 커스텀 등 다양한 레이아웃을 지원합니다. 이를 통해 다양한 종류의 데이터를 효과적으로 표시할 수 있습니다.
- 셀 재사용
    - UICollectionView는 셀을 효율적으로 관리하기 위해 셀 재사용 메커니즘을 사용합니다. 이는 메모리 사용량을 최적화하고 성능을 향상시킵니다.
- 다중 섹션
    - UICollectionView는 여러 섹션을 가질 수 있으며, 각 섹션은 여러 개의 아이템을 포함할 수 있습니다. 이를 통해 데이터를 논리적으로 그룹화하고 표시할 수 있습니다.
- 사용자 정의 가능한 셀
    - UICollectionView를 사용하여 각 셀의 모양, 크기, 배치 등을 사용자 정의할 수 있습니다. 이를 통해 다양한 디자인의 인터페이스를 구현할 수 있습니다.
- 델리게이트 및 데이터 소스
    - UICollectionView는 UITableViewDelegate 및 UITableViewDataSource 프로토콜과 유사한 UICollectionViewDelegate 및 UICollectionViewDataSource 프로토콜을 사용하여 사용자 상호 작용 및 데이터 관리를 처리합니다.

## 사용 
- iOS 애플리케이션에서 다양한 유형의 데이터를 효율적으로 표시하고 사용자 상호 작용을 처리하는 데 매우 유용합니다. 
- 주요 예로는 이미지 갤러리, 뉴스 피드, 카탈로그, 그리드 뷰 등이 있습니다.

# 주요 속성
## dataSource 
- UICollectionView 데이터를 제공하는 객체를 설정합니다. 

## delegate 
- UICollectionView의 이벤트를 처리하는 객체를 설정합니다. 

## collectionViewLayout 
- UICollectionView의 레이아웃을 설정합니다.  

## allowsSelection
- 컬렉션 뷰에서 셀 선택을 허용할지 여부를 설정합니다. 

## allowsMultipleSelection
- 여러 셀을 동시에 선택할 수 있는지 여부를 설정합니다. 

# UICollectionView 설정 
## 예제 코드
```swift
import UIKit  
  
class ViewController: UIViewController, UICollectionViewDataSource, UICollectionViewDelegate, UICollectionViewDelegateFlowLayout {  
      
    let collectionView = UICollectionView(frame: .zero, collectionViewLayout: UICollectionViewFlowLayout())  
    // 표시할 데이터 배열을 정의
    let data = ["Item 1", "Item 2", "Item 3"]  
      
    override func viewDidLoad() {  
        super.viewDidLoad()  
        // 컬렉션뷰의 프레임을 설정
        collectionView.frame = view.bounds  

        // 컬렉션뷰의 데이터 소스 및 델리게이트를 설정
        collectionView.dataSource = self  
        collectionView.delegate = self  

        // 셀 재사용을 위해 UICollectionViewCell을 등록
        collectionView.register(UICollectionViewCell.self, forCellWithReuseIdentifier: "Cell")  

        //배경색 설정 
        collectionView.backgroundColor = .white  

        //컬렉션뷰를 루트 뷰에 추가 
        view.addSubview(collectionView)  
    }  
      
    // UICollectionViewDataSource 프로토콜 메서드 
    /* [필수] 행 수를 보고합니다. */
    // section: 컬렉션뷰의 section을 나타내는 식별자 입니다. 이를 바탕으로 해당 섹션의 count를 반환합니다.
    func collectionView(_ collectionView: UICollectionView, numberOfItemsInSection section: Int) -> Int {  
        return data.count  
    }  
    
    /* [필수] 각 행에 대한 셀을 제공합니다. */
    // indexPath: 컬렉션뷰에서 Row(행)을 찾는 경로입니다. 이를 바탕으로 적절한 cell을 반환합니다.
    func collectionView(_ collectionView: UICollectionView, cellForItemAt indexPath: IndexPath) -> UICollectionViewCell {  
        let cell = collectionView.dequeueReusableCell(withReuseIdentifier: "Cell", for: indexPath)  
        // 셀의 배경색을 파란색으로 설정
        cell.backgroundColor = .blue  

        return cell  
    }  
      
    // UICollectionViewDelegate
    /* 행이 선택되었을 때 호출 */
    // indexPath: 컬렉션뷰에서 선택된 Row(행)을 찾는 경로입니다. 이를 바탕으로 어떤 행이 선택되었는지 파악할 수 있습니다.
    func collectionView(_ collectionView: UICollectionView, didSelectItemAt indexPath: IndexPath) {  
        // 선택된 항목을 콘솔에 출력
        print("Selected: \(data[indexPath.row])")  
        // 선택 표시를 해제
        collectionView.deselectItem(at: indexPath, animated: true)  
    }  
      
    // UICollectionViewDelegateFlowLayout 프로토콜 메서드
    /* 셀의 크기를 반환합니다 */
    // collectionViewLayout: 컬렉션뷰에서 사용된 레이아웃입니다. 행의 크기를 반환할 때 참고할 수 있습니다.
    // indexPath: 컬렉션뷰에서 선택된 Row(행)을 찾는 경로입니다. 이를 바탕으로 어떤 행의 크기를 반환할지 판단할 수 있습니다.
    func collectionView(_ collectionView: UICollectionView, layout collectionViewLayout: UICollectionViewLayout, sizeForItemAt indexPath: IndexPath) -> CGSize {  
        // 모든 셀의 크기를 100x100으로 설정
        return CGSize(width: 100, height: 100)  
    }  
}
```