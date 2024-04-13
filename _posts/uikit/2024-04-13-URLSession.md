---
title: "[UIKit] URLSession이란? "
excerpt: "URLSession과 예제코드"
  
categories:
  - UIKit
tags:
  - [swift, iOS, URLSession]

permalink: /UIKit/URLSession/ 
toc: true         
toc_sticky: true   
comments: true      
---
# URLSession이란? 
- Swift에서 URLSession은 네트워크 작업을 수행하기 위한 핵심 클래스입니다. 이 클래스를 사용하여 HTTP 및 HTTPS를 통한 데이터를 전송하고, 데이터를 다운로드하거나 업로드하며, 기타 네트워크 관련 작업을 처리할 수 있습니다.

# URLSession의 주요 특징
- **비동기적 네트워킹 (Asynchronous Networking)**
URLSession은 비동기적으로 네트워크 요청을 처리하므로, 네트워크 작업이 백그라운드에서 수행될 수 있습니다. 
이는 앱의 성능을 향상시키고 응답성을 유지하는 데 도움이 됩니다.
- **다양한 데이터 전송 방식 지원**
URLSession을 사용하여 데이터를 업로드하거나 다운로드할 수 있으며, JSON, 이미지, 파일 등 다양한 데이터 형식을 처리할 수 있습니다. 
이번 숙련 챕터에서의 예제는 JSON 데이터를 다운로드하여 사용합니다.
- **캐시와 쿠키 관리**
URLSession은 네트워크 응답을 캐싱하고 쿠키를 관리할 수 있는 기능을 제공합니다.

# 예제코드 
- 깃허브 API를 통해 JSON형식으로 구성된 깃허브 프로필 정보 가져와 Xcode에서 출력하는 예제입니다. 

## 1. GitHub 프로필 정보 확인 
- 아래 주소로 접속하면 데이터를 확인할 수 있습니다. 
- https://api.github.com/users/깃허브아이디

```json
{
  "login": "limlogging",
  "id": 156410026,
  "node_id": "U_kgDOCVKgqg",
  "avatar_url": "https://avatars.githubusercontent.com/u/156410026?v=4",
  "gravatar_id": "",
  "url": "https://api.github.com/users/limlogging",
  "html_url": "https://github.com/limlogging",
  "followers_url": "https://api.github.com/users/limlogging/followers",
  "following_url": "https://api.github.com/users/limlogging/following{/other_user}",
  "gists_url": "https://api.github.com/users/limlogging/gists{/gist_id}",
  "starred_url": "https://api.github.com/users/limlogging/starred{/owner}{/repo}",
  "subscriptions_url": "https://api.github.com/users/limlogging/subscriptions",
  "organizations_url": "https://api.github.com/users/limlogging/orgs",
  "repos_url": "https://api.github.com/users/limlogging/repos",
  "events_url": "https://api.github.com/users/limlogging/events{/privacy}",
  "received_events_url": "https://api.github.com/users/limlogging/received_events",
  "type": "User",
  "site_admin": false,
  "name": "HyeongSub Lim",
  "company": null,
  "blog": "",
  "location": null,
  "email": null,
  "hireable": null,
  "bio": null,
  "twitter_username": null,
  "public_repos": 10,
  "public_gists": 0,
  "followers": 5,
  "following": 8,
  "created_at": "2024-01-12T07:38:28Z",
  "updated_at": "2024-03-31T05:44:31Z"
}
```

## 2. 프로필 정보를 담을 구조체 정의 
- 깃허브 api주소에서 확인한 key 값으로 구조체 변수를 정의합니다. 
- swift에서 카멜케이스를 사용하는데 image의 경우 키 값이 avatar_url이라 CodingKey를 사용하여 카멜케이스로 변경합니다. 
- 프로토콜 
    - Codable
        - Codable은 Swift 4에서 추가된 프로토콜 
        - Codable은 Encodable과 Decodable을 결합한 것
        - 데이터를 쉽게 인코딩(직렬화) 및 디코딩(역직렬화)할 수 있도록 도와줌 
    - Encodable
        - 타입을 JSON이나 다른 형식으로 인코딩할 수 있도록 함
    - Decodable
        - JSON이나 다른 형식의 데이터를 타입으로 디코딩할 수 있도록 함

``` swift 
struct GitHubProfile: Codable {
    let login: String           // GitHub 사용자의 로그인 이름
    let profileImage: String    // GitHub 사용자의 프로필 이미지 URL

    // CodingKeys 열거형: JSON 데이터와 구조체 속성 간의 매핑을 지정
    enum CodingKeys: String, CodingKey {
        case login // login 속성은 JSON의 login 키와 매핑
        case profileImage = "avatar_url" // profileImage 속성은 JSON의 avatar_url 키와 매핑
    }
}
```

## 3. 데이터를 받아오고 저장하기 
```swift
class GitHubProfileViewController: UIViewController {
    // GitHub 사용자 프로필 정보를 가져올 URL
    let url: String = "https://api.github.com/users/limlogging"
    
    override func viewDidLoad() {
        super.viewDidLoad()
        // GitHub 프로필 정보를 가져오는 함수 호출
        getGitHubProfile(url)
    }
    
    // GitHub 프로필 정보를 가져오는 함수 정의
    func getGitHubProfile(_ urlString: String) {
        // URL 문자열을 URL 객체로 변환
        guard let url = URL(string: urlString) else { return }
        
        // URLSession 객체 생성: HTTP 요청을 수행하기 위한 세션
        let session = URLSession(configuration: .default)
        
        // 데이터 태스크 생성: 비동기적으로 URL로부터 데이터를 가져옴
        let task = session.dataTask(with: url) {
            (data, response, error) in
            if let error = error {
                // 에러가 발생한 경우 에러 메시지 출력
                print(error)
            } else if let data = data {
                do {
                    // JSON 데이터를 GitHubProfile 구조체로 디코딩
                    let gitHubProfile = try JSONDecoder().decode(GitHubProfile.self, from: data)
                    // 디코딩된 GitHub 프로필 정보 출력
                    print("login: \(gitHubProfile.login)")
                    print("profileImage: \(gitHubProfile.profileImage)")
                } catch {
                    // 디코딩 실패 시 에러 메시지 출력
                    print("Decode Error: \(error)")
                }
            }
        }
        // 데이터 태스크 시작
        task.resume()
    }
}
```

## 4. 출력결과 
```console
login: limlogging
profileImage: https://avatars.githubusercontent.com/u/156410026?v=4
```

# 마무리 
- URL: 요청할 URL 생성, GitHub API의 사용자 프로필 정보를 가져올 URL을 저장
- session: URLSession 객체를 생성하여 HTTP 요청을 수행하기 위한 세션을 설정
- dataTask: URLSession 객체를 사용하여 비동기적으로 데이터를 가져오는 데이터 태스크를 생성. 클로저를 활용하여 데이터를 받아온 후의 동작을 지정
- resume: 데이터 태스크를 시작하여 비동기적으로 데이터를 가져오는 작업을 실행