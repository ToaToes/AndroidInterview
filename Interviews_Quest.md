## 有没有自己过程线程管理？
1. Handler 和 HandlerThread
Handler：可以在主线程与后台其他线程之间传递消息和任务。使用 Handler 可以在子线程中执行任务并将结果传回主线程。
HandlerThread：是一个带有 Looper 的线程，可以在其中创建 Handler，用于处理消息。
2. Kotlin 协程
Kotlin 协程是处理异步编程的现代方法，使用简单且易于管理。通过 CoroutineScope 和 launch 函数可以轻松启动协程。

引入依赖 <br/>
使用 GlobalScope 或 lifecycleScope <br/>
定义suspend -> 使用launch

```
GlobalScope.launch(Dispatchers.Main) {
    val result = withContext(Dispatchers.IO) {
        // 执行耗时操作
    }
    // 更新 UI
}
```
3. WorkManager
WorkManager 是用于处理后台任务的推荐方式，尤其适合需要保证任务完成的场景。它可以处理定期任务和链式任务。
```
val workRequest = OneTimeWorkRequestBuilder<MyWorker>().build()
WorkManager.getInstance(context).enqueue(workRequest)
```
4. LiveData 和 ViewModel
在 MVVM 架构中，LiveData 可以与 ViewModel 一起使用，简化线程管理。ViewModel 在后台线程中处理数据，而 LiveData 会在主线程中观察数据变化并更新 UI。
5. Lifecycle-aware Components
利用 Android 的生命周期感知组件（如 LifecycleOwner），可以避免在 Activity 或 Fragment 销毁时执行线程或协程，防止内存泄漏和崩溃。


## 线程跟携程(Coroutine)有啥区别？
线程
基础概念：线程是操作系统级别(OS)的执行单元，每个线程都有自己的调用栈和局部变量。
开销：创建和销毁线程的开销相对较大，尤其是在频繁创建和销毁时。 - _Cost big_
管理：线程的管理较为复杂，需要手动处理线程的生命周期、同步、通信等问题。 - _手动处理lifecycle_
并发：可以通过多线程实现并发，但由于线程切换的开销，性能可能受到影响。 - _switch impact other thread_
协程
基础概念：协程是一种轻量级的并发机制，可以在一个线程中实现多任务的协作执行。 - _multi task in one thread-> solve multi thread problem_
开销：创建和销毁协程的开销较小，因为它们不需要独立的调用栈。 - _small cost_
管理：协程的管理更为简单，通常通过高层抽象（如 Kotlin 的 suspend 函数）来实现异步编程，代码结构更加清晰。 - _easy to control async task_
```
suspend is a keyword used to define a coroutine. It allows a function to be paused and resumed at a later time,
making it suitable for performing asynchronous tasks without blocking the main thread.

suspend fun fetchData(): String {
    // Simulate a long-running task
    delay(1000) // delay for 1 second
    return "Data fetched"
}

```
非阻塞：协程的调度是非阻塞的，可以在等待某些操作（如网络请求）时让出控制权，从而提高应用的响应性。
总结
性能：协程通常在性能和资源使用上更高效。
易用性：协程的语法更接近同步编程，代码可读性更高，维护更简单。 - _easy to read and maintain_
适用场景：如果需要进行大量的并发操作，协程是更好的选择；而对于一些底层任务或需要直接与操作系统交互的场景，线程可能更合适。 - 线程->底层交互，协程->else


## 有用过代理模式吗？ control access to another object (the real subject)
A proxy can filter, forward, or even **_delay_** the requests of the client before passing them to the target object. 
This intermediate layer can fulfill different functions, such as _access control_, _lazy initialization_, _logging_, or _caching of requests_ to enhance performance.
1. 图像加载
在移动应用中，图像加载常常是一个性能瓶颈。使用代理模式可以延迟图像的加载，直到真正需要时才加载，从而提高应用的响应速度。
2. 权限控制
在某些情况下，您可能希望限制对特定资源的访问。代理可以通过权限检查来控制访问。
3. 缓存代理
在一些应用中，您可能希望缓存某些数据以提高性能。代理可以实现缓存机制。

## 如何查内存泄露问题？<br/> 
https://github.com/ToaToes/AndroidDev---Kotlin/blob/main/Memory%20Management.md

1. 使用 Android Profiler
Android Studio 提供了内置的内存分析工具，可以实时监控应用的内存使用情况。

2. LeakCanary
LeakCanary 是一个开源的内存泄露检测库，可以帮助你自动检测内存泄露。

集成 LeakCanary：
在 build.gradle 文件中添加依赖：
```
dependencies {
    debugImplementation 'com.squareup.leakcanary:leakcanary-android:2.x'
}
```
在应用中运行后，LeakCanary 会自动检测内存泄露，并在发现时显示通知。
3. 检查代码 -> 
- 有没有用 非静态类引用 （static instance，和companion object）， 
- 有没有removeCallbacksAndMessages（custom handler to weak reference）, 
- singleton单例模式(使用activity content而不是 app content)，
- 是否使用weak reference

## 什么是 Live Data
- 是 Android Jetpack 组件中的一个类，专门用于处理和观察数据的生命周期感知（Lifecycle-aware）对象。它可以帮助开发者轻松地在应用中实现数据的观察和更新，尤其是在与 UI 组件结合时。
- 允许多个观察者订阅数据变化。当数据发生变化时，所有注册的观察者都会收到通知并更新 UI。 -> 可以简化 UI 更新逻辑。
- 可以有效防止因界面状态不一致而引发的崩溃。例如，在界面未处于活动状态时更新 UI，将不会导致空指针异常。
It is designed to hold UI-related data that can be observed within a lifecycle-aware component, such as an Activity or Fragment. <br/>
Lifecycle Awareness: LiveData is aware of the lifecycle of its observers, meaning it only updates active observers (those in the STARTED or RESUMED state). This helps prevent memory leaks and crashes due to stopped activities trying to update the UI.



## 什么是 Data Binding
- 是 Android Jetpack 组件之一，它使得 _UI 组件和数据源之间的连接更加简单和高效_ 。通过数据绑定，开发者可以直接将布局文件中的 UI 组件绑定到应用程序的数据源，从而简化代码并提高可维护性。
- 简化 UI 更新：通过数据绑定，UI 会自动更新，无需手动调用 findViewById 或设置监听器。
- 简化代码：数据绑定减少了需要编写的模板代码，例如在 UI 组件上设置数据的代码。
- UI 组件与数据源之间的双向同步。-> 双向绑定
```
在这个示例中，当用户在 EditText 中输入内容并点击提交按钮后，TextView 会显示输入的内容。

用户在 EditText 中输入内容，该内容绑定到 userInput。
点击按钮时调用 onSubmit() 方法，将 userInput 的值赋给 userName。
TextView 自动更新显示 userName 的值。
```

## 如何切换线程？
1. use coroutine
2. 使用 Handler  -> Handler 允许在特定线程中执行代码，通常用于从工作线程发送消息到主线程。 -> 适合与主线程交互
- 通过将 Runnable 与 Handler 结合使用，你可以轻松地在不同线程之间切换执行任务。
```
val handler = Handler(Looper.getMainLooper())

Thread {
    // 在后台线程中执行耗时操作
    val result = fetchDataFromNetwork()

    // 切换回主线程更新 UI
    handler.post {
        updateUI(result)
    }
}.start()

```
3. 使用 ExecutorService
通过线程池来管理多个线程。<br/>
- Running Background Tasks: For tasks that are not UI-related and can run in the background (like network requests, file I/O, etc.). 
- Handling Multiple Concurrent Tasks: To run multiple tasks at the same time and manage them efficiently.


## kotlin标准函数用过吗比如let， -> 主要用来处理可空类型 NULL  可以让代码更加简洁和易读。
https://medium.com/@khush.panchal123/if-vs-let-in-kotlin-3370077de55d <br/>
在Kotlin中，let 是一种作用域函数(higher-order function)，用于对对象执行一段代码块。它通常与可空类型一起使用，可以避免空指针异常，并使代码更加简洁。以下是 let 的主要特性和用法。
```
val result = someObject?.let { 
    // 'it' refers to someObject
    // Perform operations
    it.someMethod()
}
```
页面navigation get back
```
navController.navigate(item.id) {
    // To get back
    navController.graph.startDestinationRoute?.let { id ->
        popUpTo(id) {
            saveState = true
        }
    }
    launchSingleTop = true
    restoreState = true
}

```
Null Safety:

The expression navController.graph.startDestinationRoute?.let { id -> ... } checks if startDestinationRoute is not null. If it is not null, the block inside let is executed.
If startDestinationRoute is null, the let block is skipped, preventing any potential null pointer exceptions.

Accessing the Value:

Inside the let block, id refers to the non-null value of startDestinationRoute. This allows you to use id safely without additional null checks.

Encapsulation: (OOP的封装性)

Using let encapsulates the logic for handling the startDestinationRoute, keeping the code clean and focused. It avoids the need for a separate null check before using startDestinationRoute.

Usage:
1. Safely handle the nullable startDestinationRoute.
2. Execute the code to pop up to the specified route only when that route is available (i.e., not null).


## 线程并发一般用什么方式实现？
要么就是线程（Thread）要么就是Kotlin Coroutine

通过将 Runnable 与 Handler 结合使用，你可以轻松地在不同线程之间切换执行任务。

使用 ExecutorService 提供的线程池，简化线程管理和任务执行。

## 桌面开发里面支持哪些view，
主要就是用的jetpack compose。 
1. 基础组件
Text：用于显示文本。
Button：按钮组件。
Image：显示图像。
Icon：用于显示图标。
TextField：单行或多行文本输入框。
Checkbox：复选框。
RadioButton：单选按钮。
Switch：开关按钮。
Slider：滑动条。
2. 布局组件
Column：垂直排列子组件。
Row：水平排列子组件。
Box：允许子组件重叠，可以设置层级。
LazyColumn：支持懒加载的垂直列表。
LazyRow：支持懒加载的水平列表。
Grid：用于创建网格布局（LazyVerticalGrid 和 LazyHorizontalGrid）。
Scaffold：提供基本的页面结构，包括顶部栏、底部栏等。
3. 高级组件
Dialog：用于显示对话框。
Snackbar：用于展示短暂的信息提示。
BottomSheet：用于显示底部弹出面板。
Navigation：支持应用的导航组件，结合 NavHost 和 NavGraph。
4. 动画组件
AnimatedVisibility：用于管理组件的可见性和动画。
animate*AsState：用于对组件属性进行动画处理。

## kotlin你们主要似乎用来干嘛的?
- 多平台开发 以及 安卓开发
- kotlin for multiple platform

## 常用的数据结构李链表熟悉吗，

## Arraylist和linklist查找复杂度是什么，
数组列表（ArrayList） O(1)  - _适合频繁随机访问_ <br/>
说明: 数组列表是基于数组实现的，可以通过索引直接访问元素，因此查找元素的时间复杂度为常数时间 O(1)。你只需提供索引即可直接获取相应的元素。

链表（LinkedList）O(n) - _频繁插入和删除_ <br/>
说明: 链表是由一系列节点组成的，每个节点包含一个元素和指向下一个节点的指针。在链表中查找元素时，通常需要从头节点开始逐个遍历，直到找到目标元素，因此查找的时间复杂度为 O(n)，其中 n 是链表中节点的数量。

## 分别在什么情况下使用，
数组列表适合快速随机访问，而链表则更适合频繁的插入和删除操作。

## web前后端有没有做过跟安卓想结合的，
1. OAuth 认证 -> google firebase database
在需要用户认证的场景下，可以使用 OAuth 2.0 进行安全的身份验证。后端管理用户登录，并通过访问令牌允许 Android 应用访问保护资源。

2. RESTful API -> Retrofit and OkHttps


## 抽象工厂模式和普通工厂模式有啥区别，
普通工厂模式 -> 有一个工厂类，负责创建产品的实例。客户代码通过工厂类来获取对象。 _扩展性差_ <br/>
适用于产品种类较少且变化不大的场景。通常用在简单的对象创建上。

抽象工厂 -> 定义一个抽象工厂接口，多个具体工厂实现该接口。每个工厂可以创建一组相关的产品。 _灵活和扩展性强_ <br/>
适用于产品族（一组相关产品）较多且经常需要扩展的场景。特别是在需要保证产品的一致性时，例如 UI 组件、数据库连接等。

## 观察者模式用的多的是观察哪些？
1. 事件通知系统
在 GUI 应用中，用户的操作（如按钮点击、输入框变化）可以触发事件，观察者模式可用于处理这些事件通知。

2. 数据变化通知
在模型-视图-控制器（MVC）或模型-视图-视图模型（MVVM）架构中，当数据模型发生变化时，视图需要更新。

示例：在 Android 应用中，LiveData 和 ViewModel 结合使用，ViewModel 作为数据的源头，观察者为 UI 组件。

3. 推送通知系统
在分布式系统或实时应用中，服务器可以向多个客户端推送消息或通知。

示例：即时通讯应用中的消息通知。

## 怎么判断一个字符串是一个回文串呢
.reversed() in python

## kotlin lambda 表达式
```
val greet: () -> String = { "Hello, World!" }

fun main() {
    println(greet())  // Output: Hello, World!
}

```

```
fun main() {
    val names = listOf("Alice", "Bob", "Charlie")

    // Print each name using forEach with a lambda
    names.forEach { name -> 
        println("Hello, $name!")
    }
}

```

## Activity A to Activity B and then Back to Activity A
1. **Transition from Activity A to Activity B**
onPause(): When you start Activity B, Activity A first enters the onPause() stage. This means Activity A is still partially visible (if it has a dialog, for example) but is losing focus.
This is where you would typically pause any ongoing tasks or animations.
2. **Transition Back to Activity A**
- ```onRestart()```: This method is called when Activity A is coming back to the foreground after being stopped. This is where you can re-initialize any components that need to be set up again.
- ```onStart()```: After onRestart(), Activity A goes to the onStart() stage, indicating that it is now visible to the user but not yet in the foreground.
- ```onResume()```: Finally, Activity A transitions to onResume(), at which point it is fully active and in the foreground, ready for user interaction.
- ```onStop()```: After onPause(), Activity A transitions to onStop(), indicating that it is now completely hidden from the user. At this point, it is no longer visible on the screen.

## 有没有用过SurfaceView in compose UI
SurfaceView 是 Android 中的一种视图，它提供了一个可用于绘制和显示内容的表面，通常用于需要快速更新的图形或视频，例如游戏、视频播放和摄像头预览。

1. 独立的绘制线程：SurfaceView 允许在单独的线程中绘制内容，从而提高性能，减少主线程的负担。
2. 透明背景：它可以具有透明背景，适用于需要在其他视图上方显示内容的情况。
3. 双缓冲：SurfaceView 使用双缓冲技术，可以减少绘制时的闪烁现象。


## Retrofit and Okhttps - 代码简单  - Retrofit 通常是基于 OkHttp 构建的，利用 OkHttp 提供的功能来处理底层的网络请求
1. Retrofit 是一个类型安全的 HTTP 客户端，用于 Android 和 Java。它简化了与 REST API 的交互，使开发者能够通过注解来定义 API 接口，从而更容易地发送网络请求并处理响应。
2. OkHttp 是一个高效的 HTTP 和 HTTP/2 客户端，用于 Android 和 Java。它为网络请求提供了底层支持，并且处理请求和响应的性能非常出色。

## 什么是 LaunchEffect in Kotlin
LaunchedEffect 是 Jetpack Compose 中用于处理副作用的一个函数，主要用于在组合过程中启动协程。它是一个组合函数，可以在其范围内执行协程代码，并且会在指定的键值发生变化时重新启动。
```
import androidx.compose.runtime.*
import kotlinx.coroutines.delay

@Composable
fun MyComponent() {
    var count by remember { mutableStateOf(0) }

    // 每当 count 变化时，启动这个副作用
    LaunchedEffect(count) {
        // 执行一些异步操作
        delay(1000)  // 模拟网络请求
        println("Count is now: $count")
    }

    // UI 组件
    Button(onClick = { count++ }) {
        Text("Increment Count")
    }
}

```

## Launch 和 LaunchEffect 的区别
Launch - 适合非UI操作
LaunchEffect - 适合UI操作

## 动画模组 in kotlin


