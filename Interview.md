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
Modern Runtime: ART replaced Dalvik starting with Android 5.0 (Lollipop). <br/>
Dalvik use Just-In-Time (JIT) Compilation: It used JIT compilation, meaning that the code is compiled into machine code at runtime. This can lead to slower performance because the compilation happens as the app runs.<br/>
ART use Ahead-Of-Time (AOT) Compilation: ART uses AOT compilation, which compiles the app’s bytecode into machine code when the app is installed. This leads to faster startup times and improved runtime performance.<br/>
Also ART has better memory management and garbage collection managment than Dalvik.

## 4. What is the difference between StateFlow and SharedFlow


## 5. Change Screen to orientation/horizontal
Changing the screen orientation from horizontal (landscape) to vertical (portrait) in an Android app triggers a configuration change. <br/>
This causes the activity to be destroyed and recreated, which means the activity lifecycle methods (onPause(), onStop(), onDestroy(), onCreate(), and onResume()) will be called again.

If you want to handle configuration changes without destroying the activity, you can override the default behavior by specifying configChanges in the manifest for the activity. <br/>
However, this approach is generally not recommended unless you have a specific reason, as it can complicate state management.

To save the UI state during a configuration change, you can use ```onSaveInstanceState()``` and ```onRestoreInstanceState()```.

不设置Activity的android:configChanges时，切屏会重新回调各个生命周期，切横屏时会执行一次，切竖屏时会执行两次。 </br>
设置Activity的android:configChanges=”orientation”时，切屏还是会调用各个生命周期，切换横竖屏只会执行一次 设置Activity的android:configChanges=”orientation |keyboardHidden”时，切屏不会重新调用各个生命周期，只会执行onConfigurationChanged方法

## 6. 线程池 in Android
Used to use **Async** which is now deprecated, 在Android 11及以后版本中已被弃用。它主要用于执行短时间的后台任务，并在任务完成后更新UI。<br/>
Now use **Kotlin Coroutines** instead, or It's recommended to use alternatives like ExecutorService, HandlerThread, or more modern solutions like LiveData, ViewModel

## 7. What is handler in Android
A Handler in Android is a utility that allows you to send and process Message and Runnable objects associated with a thread's **MessageQueue**. 
It is primarily used for managing threads and communication between the main UI thread and background threads.

**Key Features of Handlers:** 交流性 顺序性 延迟性
1. Thread Communication: Handlers can post messages and runnable tasks to be executed on the thread associated with the handler, **usually the main (UI) thread**.

2. Message Queuing: Handlers allow you to enqueue messages and runnables to be processed **in the order they are received**.

3. Delayed Execution: You can schedule messages and runnables to be executed **after a specified delay**.

Common Methods: <br/>
```post(Runnable r)```: Queues a runnable to be run on the thread to which the handler is attached. <br/>
```postDelayed(Runnable r, long delayMillis)```: Queues a runnable to be run after a specified delay. <br/>
```sendMessage(Message msg)```: Sends a message to the handler, which can then be processed in the handleMessage(Message msg) method. <br/>
```sendEmptyMessage(int what)```: Sends a message with no data.

Use Cases:<br/>
1. Updating the UI from a background thread.
2. Managing delayed tasks or periodic updates.
3. Handling messages and events in a thread-safe manner.

Important Note:<br/>
When using handlers, be mindful of memory leaks. It's often a good practice to remove callbacks and messages in onDestroy() or when they're no longer needed, especially when working with activities or fragments.<br/>

