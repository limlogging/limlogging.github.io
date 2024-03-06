---
title: "[Swift] 변수와 상수 "
excerpt: "변수(값 변경 가능) var, 상수(값 변경 불가능) let "
  
categories:
  - swift
tags:
  - [swift, variable, constant]

permalink: /swift/variableAndConstant/ 
toc: true           #On this page 보이기 
toc_sticky: true    #on this page 스크롤에 따라 움직이도록 
comments: true      #댓글
---

### 변수와 상수 

- 변수나 상수를 이용하여 프로그램에서 사용되는 데이터를 메모리에 저장합니다. 

```swift
let a: Int = 1
let b: Int = 2
```

### 변수 
- 생성 후 데이터 변경 가능합니다.  
- var 변수명: 데이터 타입 = 값  
```swift
var myMoney: Int = 10000 //현재 내 돈 만원
myMoney = 20000 // 알고보니 이만원, 이만원으로 수정  
```

### 상수 
- 한번 값을 설정하면 다음에 변경 할 수 없습니다. 
- let 상수명: 데이터 타입 = 값 
```swift
let tenWon: Int = 10 //10원  
tenWon = 20          //에러 발생 10원은 10원   
```
상수로 선언된 10원을 20원으로 수정하면 에러가 발생합니다. 
let을 var로 변경하여 값을 변경 가능하게 만들어야합니다. 

### 상수 값 변경 시 에러 
``` console
error: MyPlayground.playground:60:1: error: cannot assign to value: 'tenWon' is a 'let' constant
tenWon = 20
^~~~~~

MyPlayground.playground:59:1: note: change 'let' to 'var' to make it mutable
let tenWon: Int = 10
^~~
var

```