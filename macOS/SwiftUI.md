# Tuist-Template (macOS - SwiftUI)
### Setting
Tuist -> ProjectDescriptionHelpers -> Environment.swift
로 가셔서 
```swift
import ProjectDescription

public enum Environment {
    public static let appName = \(앱 이름)
    public static let targetName = \(타겟 이름)
    public static let targetTestName = "\(targetName)Tests"
    public static let organizationName = \(사용자 이름)
    public static let deploymentTarget: DeploymentTarget = .macOS(targetVersion: "11.0")
    public static let platform = Platform.macOS
    public static let baseSetting: SettingsDictionary = SettingsDictionary()
}
```
& 

Tuist -> ProjectDescriptionHelpers -> CodeSign.swift 이동
```swift
import ProjectDescription

public extension SettingsDictionary {
    static let codeSign = SettingsDictionary()
        .codeSignIdentityAppleDevelopment()
        .automaticCodeSigning(devTeam: " 사용자의 Apple developer ID Code")
}
```

Tuist -> Projects -> 앱 이름 -> Sources -> App -> App.swift
```
import SwiftUI
import RootFeature

@main
struct (앱 이름)App: App {
    var body: some Scene {
        WindowGroup {
            RootView()
        }
    }
}
```

이런식으로 바꿔주시면 됩니다.

### Make File 사용법
- make generate
    - tuist fetch 이후 tuist generate 함
- make clean
    - **/*.xcodeproj 과 *.xcworkspace 모두 삭제
- make reset
    - tuist clean 후 **/*.xcodeproj 과 *.xcworkspace 모두 삭제
- make feature
    - 새로운 Feature 생성 
    - make feature를 실행한 후 새로운 Feature 이름 입력

### Graph

<img src = "https://user-images.githubusercontent.com/68891494/199053153-75e52cfd-1103-4447-8a52-03e2cddc0120.png">
