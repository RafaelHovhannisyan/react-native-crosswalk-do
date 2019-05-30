# react-native-webview-crosswalk-do

#### Forked from [jordansexton](https://github.com/jordansexton). Not contributed for two years. Some bugs fixed and added dynamic build.gradle(which taking android compile and sdk versions from ext object)

[![npm licence](http://img.shields.io/npm/l/react-native-webview-crosswalk.svg?style=flat-square)](https://npmjs.org/package/react-native-webview-crosswalk "View this project on npm")

### Latest Dependencies

*  `react-native >=0.59.8`, `react >= 16.8.3`

### Installation

* From the root of your React Native project

```shell
npm install react-native-crosswalk-do --save

node_modules/react-native-crosswalk-do/libs/xwalk_core_library-23.53.589.4-arm.aar 
to your 
android/app/libs
```

### Include module in your Android project

* In `android/setting.gradle`

```gradle
...
include ':CrosswalkWebView', ':app'
project(':CrosswalkWebView').projectDir = new File(rootProject.projectDir, '../node_modules/react-native-crosswalk-do')
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
  implementation (name: "xwalk_core_library-23.53.589.4-arm", ext: "aar")     // <--- add this line
  implementation project(':CrosswalkWebView')                             // <--- add this line
}
```

* Register package, sdd code into MainApplication.java:

```java
import com.rafaelhovhannisyan.react.crosswalk.webview.CrosswalkWebViewPackage;    // <--- add this line

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
