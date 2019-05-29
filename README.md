# react-native-webview-crosswalk-do

#### Forked from [jordansexton](https://github.com/jordansexton). Not contributed for two years. Some bugs fixed and added dinamic build.gradle(which taking android compile and sdk versions from ext object)

[![npm licence](http://img.shields.io/npm/l/react-native-webview-crosswalk.svg?style=flat-square)](https://npmjs.org/package/react-native-webview-crosswalk "View this project on npm")

### Latest Dependencies

*  `react-native >=0.59.8`, `react >= 16.8.3`

### Installation

* From the root of your React Native project

```shell
npm install react-native-webview-crosswalk-do --save
mkdir android/app/libs
cp node_modules/react-native-webview-crosswalk/libs/xwalk_core_library-22.52.561.4.aar android/app/libs/
```

### Include module in your Android project

* In `android/setting.gradle`

```gradle
...
include ':CrosswalkWebView', ':app'
project(':CrosswalkWebView').projectDir = new File(rootProject.projectDir, '../node_modules/react-native-webview-crosswalk-do')
```

### Include libs in your Android project

* In `android/build.gradle`

```gradle
...
allprojects {
    repositories {
        mavenLocal()
        jcenter()

        flatDir {          // <--- add this line
            dirs 'libs'    // <--- add this line
        }                  // <--- add this line
    }
}
```

* In `android/app/build.gradle` (I guess in latest version you don't need to add)

```gradle
...
dependencies {
  ...
  compile (name: "xwalk_core_library-22.52.561.4", ext: "aar")     // <--- add this line
  compile project(':CrosswalkWebView')                             // <--- add this line
}
```

* Register package, sdd code into MainApplication.java:

```java
import com.rafael.hovhannisyan.react.crosswalk.webview.CrosswalkWebViewPackage;    // <--- add this line

public class MainApplication extends Application implements ReactApplication {
  ......

  @Override
  protected List<ReactPackage> getPackages() {
    return Arrays.<ReactPackage>asList(
        new MainReactPackage(),
        new CrosswalkWebViewPackage()    // <--- add this line
    );
  }

  ......

}
```

## License
MIT
