---
title: "[UIKit] LifeCycle - 생명주기"
excerpt: "LifeCycle - 애플리케이션과 앱의 다양한 객체들이 어떻게 생성되고, 표시되고, 사용되고, 제거되는지에 관한 개념"
  
categories:
  - UIKit
tags:
  - [swift, iOS, LifeCycle]

permalink: /UIKit/LifeCycle/ 
toc: true         
toc_sticky: true   
comments: true      
---

# 생명주기(LifeCycle)
- UIKit에서의 라이프사이클은 애플리케이션과 앱의 다양한 객체들이 어떻게 생성되고, 표시되고, 사용되고, 제거되는지에 관한 개념입니다.

# App LifeCycle 
![App LifeCycle](/assets/images/categories/uikit/2024-03-18-AppLifeCycle.png)

## Not Running 
- 실행되지 않거나  종료된 상태.

## InActive
- 앱이 Foreground 상태로 돌아가지만, 이벤트는 받지 않는 상태, 잠시 존재하는 상태.
- 아래에서 위로 스와이프 하는 순간 `InActive` 상태가 된다.

## Active
- 일반적으로 앱이 돌아가는 상태(이벤트를 받는 단계)
- Background 상태에서 여러 작업 수행

## Background
- 앱이 `Suspended`(유예 상태) 상태로 진입하기 전 거치는 상태 (음악, 통화 앱 같은 경우는 background)

## Suspended
- 앱이 Background 상태에 있지만, 아무 코드도 실행하지 않는 상태.
- 시스템이 임의로 Background 상태의 앱을 Suspended 상태로 만든다.(리소스 해제)
- Not Running 과 일반적으로 동일

<br>

# UIViewController LifeCycle
![UIViewController LifeCycle](/assets/images/categories/uikit/2024-03-18-UIViewControllerLifeCycle.png)

## init()
- UIViewController 객체가 생성

## loadView()
- 컨트롤러의 뷰 계층 구조가 생성

## viewDidLoad()
- 뷰 계층 구조가 메모리에 로드되었으며, 초기화 작업을 수행

## viewWillAppear()
- 뷰가 화면에 나타나기 직전에 호출. 뷰를 업데이트하거나 애니메이션을 시작

## viewDidAppear()
- 뷰가 화면에 나타나면 호출. 애니메이션을 종료하거나 뷰의 상태를 업데이트

## viewWillDisappear()
- 뷰가 화면에서 사라지기 직전에 호출. 데이터를 저장하거나 애니메이션을 시작

## viewDidDisappear()
- 뷰가 화면에서 사라지면 호출. 애니메이션을 종료하거나 뷰의 상태를 업데이트

## deinit
- UIViewController 객체가 메모리에서 해제

# 예제 코드 
```swift
class MyViewController: UIViewController {
    
    override init(nibName nibNameOrNil: String?, bundle nibBundleOrNil: Bundle?) {
        super.init(nibName: nibNameOrNil, bundle: nibBundleOrNil)
        // 초기화 메서드에서 필요한 작업 수행
    }
    
    required init?(coder: NSCoder) {
        super.init(coder: coder)
        // 초기화 메서드에서 필요한 작업 수행
    }
    
    override func loadView() {
        // 뷰를 직접 생성하여 할당
        self.view = UIView()
    }
    
    override func viewDidLoad() {
        super.viewDidLoad()
        // 뷰에 대한 추가 구성 작업 수행
    }
    
    override func viewWillAppear(_ animated: Bool) {
        super.viewWillAppear(animated)
        // 뷰가 나타나기 전에 수행할 작업 수행
    }
    
    override func viewDidAppear(_ animated: Bool) {
        super.viewDidAppear(animated)
        // 뷰가 나타난 후에 수행할 작업 수행
    }
    
    override func viewWillDisappear(_ animated: Bool) {
        super.viewWillDisappear(animated)
        // 뷰가 사라지기 전에 수행할 작업 수행
    }
    
    override func viewDidDisappear(_ animated: Bool) {
        super.viewDidDisappear(animated)
        // 뷰가 사라진 후에 수행할 작업 수행
    }
    
    deinit {
        // 뷰 컨트롤러가 메모리에서 해제되기 전에 수행할 작업 수행
    }    
}
```