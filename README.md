# react-native-alipay-levinqdl

React Native Module for alipay.com

## install

```
npm install react-native-alipay-levin --save
```

## Android

### With rnpm

```
rnpm link react-native-alipay-levin
```

### Manually

* android/settings.gradle

```
include ':react-native-alipay-levin'
project(':react-native-alipay-levin').projectDir = new File(rootProject.projectDir, '../node_modules/react-native-alipay-levin/android')
```

* android/app/build.gradle

```
dependencies {
    compile project(':react-native-alipay-levin')
}
```

* register module (in MainActivity.java)

```java
...

import com.levinqdl.alipay.AlipayPackage; // <--- IMPORT

public class MainActivity extends ReactActivity {

    ...

    @Override
    protected List<ReactPackage> getPackages() {
        return Arrays.<ReactPackage>asList(
            new MainReactPackage(),
            new AlipayPackage() // <--- ADD HERE
        );
    }
}
```

## iOS

### With rnpm

```
rnpm link react-native-levin-alipay
```

### Manually

> Link `AlipayModule` library from your `node_modules/react-native-alipay-levin/ios` folder like its [described here](http://facebook.github.io/react-native/docs/linking-libraries-ios.html). Don't forget to add it to "Build Phases" of project.

### Config

* Added the following libraries to your "Link Binary With Libraries":
  * [x] CoreMotion.framework
  * [x] CoreTelephony.framework
  * [x] libc++
  * [x] libz
  
* add `URL Schema` as your app id for `URL type` in `Targets - info`
* Make sure you have these code in AppDelegate.m to enable callback

```objective_c
#import "AlipayModule.h"
```

```objective_c
- (BOOL)application:(UIApplication *)application openURL:(NSURL *)url
  sourceApplication:(NSString *)sourceApplication annotation:(id)annotation
{
  [AlipayModule handleCallback:url];
  return YES;
}
```

### General Usage

```javascript
import Alipay from 'react-native-alipay-levin';

```

```javascript
Alipay.pay("signed pay info string").then(function(data){
                    console.log(data);
                }, function (err) {
                    console.log(err);
                });

```
