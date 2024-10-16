# AndroidInterview
Some Interview hints

## 1. What is Android
Based on Linux kernal, operating systems for mobile devices. </br>
It is based on the Linux kernel and offers a rich application framework that allows developers to create apps using Java, Kotlin, and other languages.

## 2. Android Version (What is the latest Android version)
2024
targetSdk = 34: Where the app is been tested against, Google play has least requirement for targetSdk <br/>
compileSdk = 34: where the app is been compiled against, cant be lower than targetSdk <br/>
minSdk = 24: Least low version the app supports Sdk lib <br/>

## 3. What is Dalvik? What is ART, what difference
Both runtime environment for Android to execute applications. <br/>
Modern Runtime: ART replaced Dalvik starting with Android 5.0 (Lollipop).

## 4. 

## 5. 
changing the screen orientation from horizontal (landscape) to vertical (portrait) in an Android app triggers a configuration change. <br/>
This causes the activity to be destroyed and recreated, which means the activity lifecycle methods (onPause(), onStop(), onDestroy(), onCreate(), and onResume()) will be called again.

If you want to handle configuration changes without destroying the activity, you can override the default behavior by specifying configChanges in the manifest for the activity. <br/>
However, this approach is generally not recommended unless you have a specific reason, as it can complicate state management.

To save the UI state during a configuration change, you can use onSaveInstanceState() and onRestoreInstanceState().

不设置Activity的android:configChanges时，切屏会重新回调各个生命周期，切横屏时会执行一次，切竖屏时会执行两次。 </br>
设置Activity的android:configChanges=”orientation”时，切屏还是会调用各个生命周期，切换横竖屏只会执行一次 设置Activity的android:configChanges=”orientation |keyboardHidden”时，切屏不会重新调用各个生命周期，只会执行onConfigurationChanged方法

