Amplify dependencies can be installed with Swift Package Manager. Open your iOS project in Xcode.

1. Open **Package Dependency** by selecting **File** > **Swift Packages** > **Add Package Dependency...**

2. Enter the Amplify iOS GitHub repository URL in the **search bar**:
```
https://github.com/aws-amplify/amplify-ios
```

3. Select the **Version** option for the Rules and click **Next**

4. Select the following plugins:
- Amplify
- AWSPluginsCore
- AWSDataStorePlugin
- AWSAPIPlugin

5. Go to **<YOUR_APP_NAME>App.swift** and add the following lines to initialize Amplify libraries:
```swift
import Amplify
import AWSDataStorePlugin
//import AWSAPIPlugin // UNCOMMENT this line once backend is deployed
```

```swift
:::NO_COPY:::
@main
struct <YOUR_APP_NAME>App: App {
```
```swift
    public init() {
        let dataStorePlugin = AWSDataStorePlugin(modelRegistration: AmplifyModels())
        //let apiPlugin = AWSAPIPlugin(modelRegistration: AmplifyModels()) // UNCOMMENT this line once backend is deployed

        do {
            try Amplify.add(plugin: dataStorePlugin)
            //try Amplify.add(plugin: apiPlugin) // UNCOMMENT this line once backend is deployed
            try Amplify.configure()
            print("Initialized Amplify");
        } catch {
            print("Could not initialize Amplify: \(error)")
        }
    }
```
```swift
:::NO_COPY:::
}
```
