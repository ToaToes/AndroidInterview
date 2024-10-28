1. Which of the following statements are valid regarding the management of Android's Content Providers?
- Content Providers must declare authorities in AndroidManifest. xm1 if other applications are using them.
- Content Providers present data to external applications as one or more relational database-like tables.
- Applications instantiate a Content Provider and deal with the provider to access a Content Provider's data.
- Activities register just one Content Provider.
- Content Providers must use the SQLite database system for internal data management.


2. Which of the following are reasons to use a DialogFragment in placelof accessing an Alert Dialog in new Android applications?
- Dialog state management is handled by the underlying Application Programming Interface (API), rather than the developer.
- A DialogFragment includes more default buttons than an Alert Dialog.
- The Activity. showDialog () method is deprecated as of Application Programming Interface (API) level 15.
- Using AlertDialog requires more memory than using a DialogFragment.
- The FragmentManager restores the dialog after a configuration change.


3. Which of the following statements regarding the Kernel/Application sandbox in Android are valid?
- The kernel and core applications run with root permissions by default.
- Each application receives a dedicated part of the filesystem where applications read and write private data without requesting additional permissions.
- A memory corruption error in an application affects the memory, or allow arbitrary code execution, of another application.
- The Application sandbox is optional for Native Code.
- I The Application sandbox is optional for applications.


4. A company has defined strings in the resource file /res/values/corp_string values.ml. One of the Android application's activities is showing a compile resource not found error when trying to access .string.error msg. Which of the following are solutions to resolve this issue?
Add the string resource name 'error msg' to the corp string values. xmI file if the resource does not exist.
Move the corp string values.xm1 file to res /xml/ subfolder.
Add the activity definition to the AndroidManifest. xml file.
Rename the corp string.xm1 file to strings. xml.
Change the application code to access R. corp string.error msg instead of R. string. error msg.


5. when view model no longer used and is destroy in android, what methods will be called,  - its onCleared()


6. Which of the following are differences between local and instrumented tests in Android?
Local tests execute on the host system, while instrumented tests execute on a physical device.
Local tests focus on user interaction assertions, while instrumented tests focus on method invocation assertions.
Local tests are unreliable due to issues including memory availability and external application dependencies.
Local tests check connectivity with external data sources, while instrumented tests check individual unit functionality.
Local tests rely on automated testing techniques, while instrumented tests rely on manual testing techniques.



7. Which of the following are valid fundamental menu types applicable in Android?
Checkbox menu
Notification menu
Context menu
Drop-down menu
Options menu


8. Which of the following techniques will NOT provide enhanced location updates on Android version 8.0 and above systems?
Send the application or service to the foreground whenever updates are required.
I Register a passive location listener.
Rely on the GeofencingClient.
Employ startForegroundService () to start a foreground service.
Use the non-batched version of the Fused Location Provider API elements.


9. Which of the following statements regarding an Android Service component are NOT valid?
Performs long-running operations in the background.
A service continues to run when the user switches applications.
Provides a user interface.
A service performs multiple tasks, such as playing music and downloading files, without user interaction.
Causes blocking within an application when long-running operations are performed within the service.


10. Which of the following statements are valid regarding Android Intent objects?
Messaging objects used to request an action from another component.
• UI components used to invoke or start Activities.
Provide data between the calls to an individal Activity's life cycle.
Declare an applications need for a resource prior to application installation.
Convey information about the Android device to other applications.



11. A dialog-based application must run on multiple APIs and have the matching appearance for each API based on the underlying operating system. Which of the following ensures the theme will match the underlying operating system in Android?
<activity android: theme="@style/CustomTheme">
<activity android: theme="@android: style/Theme. Dialog.Alert"›
<application android: theme-"@android: style/Theme. Dialog"› <application android: them&-"android: Theme.Dialog.Alert "› <application android: theme= "@android: Theme. Dialog"›


12. Which of the following are features of the standard Android toast object used to display messages to the user?
Toast messages are preferred over snackbar messages when the snackbar timeout is too short to ensure users see the message.
Toast messages are shown for varying lengths of time.
Toast messages are dismissed when the application user closes the toast messages.
Toast messages force the user to acknowledge the messages displayed.
Toast messages are positioned to appear at a specified location on screen.


13. Which of the following statements describe the purpose of a broadcast in Android?
Share system wide events.
React to the NETWORK_STATE_ CHANGED ACTION broadcast, providing a user's location and personally identifiable data.
Start activities.
Publish app-specific events using the sendOrderedBroadcast (Intent, String) method.
Modify the BROADCAST ACTIONS. TXT file to contain application-specific intents.


14. Which of the following replacements for ** ** * will allow the Android code below to retrieve the current internet connectivity status?
val connManager =
context.getSystemService (Context.CONNECTIVITY_SERVICE)
as ConnectivityManager
val activeNetwork: NetworkInfo? = connManager.activeNetworkInfo
****
val isConnected ? activeNetwork.isConnectedOrConnecting : false
m
val isConnected = activeNetwork?.isConnectedOrConnecting?: false

var isConnected = false
if (activeNetwork != null) ‹
isConnected = activeNetwork.isConnectedOrConnecting
val isconnected = activeNetwork . isconnectedorconnecting
val isConnected: Boolean = activeNetwork?. isConnectedOrConnecting == true



15. Which of the following describe the ShareActionProvider in Android?
An API for calling a definable group of providers shared among the same application.
Creates views enabling data sharing.
Shares data between activities via the SharedPreference object.
An API for calling button actions shared among the Android device applications.
An API for calling a definable group of actions shared among the same application.


16. Which of the following method calls will create a notification connecting a media session to the media controls for an Android application?
val notification = Notification. Builder (this@PService, CHANNEL ID
       setStyle (mediaStyle)
       setSmallIcon (R.drawable.ic app logo)
.build ()
_ val notification - Notification. Builder (this@PService) . setSession (mediaSession)
• setSmallIcon (R.drawable.ic app logo)
val notification = Notification. Builder (this@PService, CHANNEL_ID)
.setSession (mediaSession)
. setSmallIcon (R. drawable.ic_app_logo)
.build ()

val notification = Notification. Builder (this@PService, CHANNEL_ ID)
.setStyle (mediaStyle)
* ﻿﻿setSmallIcon (R.drawable.ic app logo)
* ﻿﻿val notification = Notification. Builder (this@PService)
setsession (mediasession)
. setSmallIcon (R.drawable.ic app logo)
.build ()



17. An HTTP-networked application functions on fast Internet connections and on slow connections the application is unable to connect to the server. Which of the following are valid solutions for preventing this issue?
Reduce data sent back from the server to smaller packets for faster processing.
Check the ULConnect ion class used and set the . getConnectTimeout () to a higher value.
Add the <uses-permission android:name-"android.permission.ACCESS NETWORK STATE" /> to the AndroidManifest.xm1 file, and then in code query the state of the network to see if it is connected.
Modify the connection object to retry the connection more times.
Check the URLConnect ion class used and set the . get ReadTimeOut () to a higher value.



18. Which of the following Kotlin code snippets will output the letters A, D, G, and J in Android?
for (value in 1. rangeTo (10) step 3) {
print ( (value + 64) . toChar () )
• for (num in 65 until 74 step 3) f print (num.toChar () )
for (letter in "A".."J" step 3) {
print (letter)
for (value in 1. .10 step 3)
{
print ( (value + 65) . toChar () )
for (letter in "A".rangeTo (10) step 3) t
print (letter)



19. Which of the following statements describe Android's WakeLock feature?
Any application using a WakeLock must request the android.permission. WAKE _LOCK in the AndroidManifest. xml.
An exception will be thrown if an application calls acquire () on a WakeLock and the life cycle method onDestroy () is invoked without the application calling release () on the acquired WakeLock.
A WakeLock allows an application to have the device running on maintain power to the Central Processing Unit (CPU) when the device would go to sleep.
To use a WakeLock, create an instance of it with new and call it with the invoke method.
An alternative to using a WakeLock when a video application must keep the screen active is to set the WindowManager. LayoutParams. FLAG_ KEEP_SCREEN_ON flag



20. An Android application takes the user's current position and converts the position to a physical address using the Geocoder API getFromLocation () method in the main thread. Users have reported the application is throwing an Application Not Responding (ANR) error. Which of the following cause this issue?
The user's precise location is not known and the application is waiting for a location update.
The call to get FromLocation () relies on a network lookup, which requires too much time.
The locale has not been set properly on the GeoCoder object and the location address call is hanging.
The users experiencing the AN error are not connected to the Internet at the time of the error.
The user is not using GPS for location updates.



21. Which of the following describe the relationship between Android and Linux?
At the system level, Android's process, memory, and security management is identical to any other Linux system.
• Any Linux installation will run Android without modification or enhancement.
Every Android application runs multiple Linux processes.
Each Android application runs as a separate Linux user.
Android smartphones grant Linux features to users.



22. Which of the following are examples of building an explicit intent in Android?
Uri uri = Uri.parse ("www .example.com"');
Intent intent = new Intent (Intent.ACTION VIEW, uri);
Intent intent = new Intent (this, MyActivity.class);
Intent intent = new Intent () ;
intent.setIntent ("com. example. app",
"com. example. app.MyActivity");
Intent intent = new Intent ( );
intent.setAction (Intent.ACTION SEND);
intent .putExtra (Intent •EXTRA_IEXT,"text");
Intent intent = new Intent (Intent.ACTION SEND);
Intent chooser
= Intent.createChooser (intent, "Chooser");


23. Which of the following statements regarding Android's Permissions system are valid?
Permissions are declared in the AndroidManifest.xml.
If an application is granted all required permissions when installed, permissions will be uninstalled and installed again without the user having to agree to the permissions again.
I The permissions an application requires are shown to users before initial installation.
If no permissions are declared in AndroidMani fest. xml, an application will have none assigned, including the ability to run.
The full set of permissions provided by Android are assigned by default to an application which has not requested specific permissions.



24. Which of the following identify the error in the code below, representing a navigation drawer following standard Android design principles?
<android.support. v4.widget. DrawerLayout android:layout_width="match parent" android: layout_height="match parent"
<FrameLayout
android:layout width="240dp" android: layout height="match parent" />
<ListView
android:layout width="match parent" android:layout height="match parent" android:layout gravity-"left"/>
</android. support. v4.widget.DrawerLayout>
Modify the FrameLayout height to 240dp.
Set the ListView layout gravity to "start" to support languages reading right-to-left.
Switch the FrameLayout width and the list layout width values to allow the main content window to match the parent width.
Specify an android: layout gravity for the Drawer Layout element.
Change the ListView layout height to 240dp.



25. After adding a new AndroidX component to an Android application, the build of the application results in a Gradle sync error. Which of the following solutions will fix this problem?
Delete mavenCentral () from the list of repositories in the build. gradle file.
Set android.useAndroidx=true in the gradle.properties file.
Choose File > Invalidate Caches/Restart from the Android Studio menu.
Update the existing Android components to the latest versions.
Ensure the AndroidX component addition is the latest version.



26. An Android application defines a custom toast layout in the file toast layout. ×ml which contains the code below. Which of the following code blocks enable the toast?
<LinearLayout
xmlns: android-"http: / /schemas.android.com/apk/res/android"
android:id="@+id/my_layout" android:orientation="horizontal"
android:layout width="match parent" android:layout height="match parent"
>
</LinearLayout>



27. An Android application activity initiates resources which are time-consuming to create in onCreate () . These resources are kept in memory to increase application performance. Other applications do not run while this application is running and are placed in the background and not visible, due to a lack of device resources, including memory. Which of the following solutions fix this issue?
The Activity must move resource initialization to onResume () instead of onCreate () and remove resources in onPause () .
The Activity must release all resources in the onDestroy () method call and recreate the resources in onStart ().
The Activity must save the state on on Pause () , release all resources in onStop () and reinitialize necessary resources in onStart () .
The Activity must release all resources in the onDestroy () method call and recreate the resources in onResume () .
The Activity must release all resources in the on Pause () method call.




28. Which of the following are valid statements regarding GPS and Network location awareness in Android?
GPS requires more power than Network location updates.
Network location updates are not available indoors.
Either GPS or Network location updates are used in an Android application, but never both.
Network location updates respond faster than GPS updates.
GPS is more accurate than Network location updates.


29. Which of the following Android permissions are requested by third-party applications?
READ CONTACTS
LOCATION HARDWARE
SET TIME ZONE
READ EXTERNAL STORAGE
READ CALENDAR



30. An Android application requires an activity presenting the user with a view containing two buttons, each filling half of the screen regardless of screen size. Which of the following layout file XML attributes must be added to accomplish this?
A Linear Layout root element with android:orientation="horizontal ".
One button element with the attribute android: gravity="left", the other element with the attribute android:gravity="right"
A Linear Layout root element with android:orientation="vertical".
Button elements with the attribute android: layout weight="1"
Button elements with the attribute android:layout width=".5"



31. An organization has an application to test and requires decoupling of the functions, classes, and modules. Which of the following techniques will make the decoupling process occur in Android?
Use direct framework dependencies in classes containing business logic.
Create dependencies to replace using interface structures.
Rely on integration tests and User Interface (UI) tests on classes.
Split the application into layers or modules.
Keep entities with large dependencies out of activities and fragments.



32. Which of the following objectives are achieved using Android's Content Providers?
Retrieving data from the shared preferences within an application.
Retrieving entries from the Android Keystore.
Accessing the content of an SMS via the Android SMS application's data.
Accessing the Contacts database from an application.
Providing encapsulated, secure access to application custom search suggestions.



33. An Android developer must apply a different look and feel to each of the edit boxes in an application. Which of the following actions fulfill this requirement?
Define a theme in the Android Manifest file as an activity attribute.
Replace each edit box XML definition with a custom-defined edit box Java implementation extending the EditTextBox.
Define a theme and have all edit boxes in the layout files use the theme.
Create custom drawables for each edit box and place the drawables in the /res/drawable/ folder.
Define multiple style elements and have each edit box use a particular style.



34. To conserve power while using GPS to get position updates, an Android developer implements a LocationListener with location updates based on either 7.5 minutes between updates or a GPS location change of greater than 500 meters (1640 feet). Which of the following replacements for ***** in the code below will achieve this?
locationManager.requestLocationUpdates (
****)；




35. An application must perform work in the background to fill out the content of a layout. Which of the following strategies will ensure the coroutine is canceled when the layout is canceled?
Write a LifeCycle scope where the coroutine appears within a lifecycleScope. Launch call.
Add an onViewCreated () method to a ViewMode1 scope to monitor the layout status.
Develop a ViewMode1 scope where the coroutine appears within a repeatOnViewModel call.
Launch a new Corout ineScope, keep the reference to a Job, and cancel the job inside the corresponding callback (onDestroy, onStop).
Create a LifeCycle scope where the coroutine appears within a repeatOnLi fecycle call.



36. A hybrid cloud/mobile application is throwing NetworkOnMainThreadException in an activity when trying to POST a request with a
JSON data object to the cloud. Which of the following situations cause this error?
Incorrect permissions assigned to the AndroidMani fest. xm1 file.
The code which sends the JSON object to the server is in the onResume () method in the activity.
The server URL accessed for the post'request is invalid.
An async task is making the call to send the JSON data object back in its do InBackground () method.
The connection object used to send the POST request has failed to connect to the server.



37. Users of an application with a targetSdkVersion=21 must know why the permission (USE FINGERPRINT) is required while trying to install the application from Google Play on Android versions 23+ even though SD Version 21 does not support this permission. The released application does not declare this permission, nor does the application need the permission. Which of the following provide a valid fix?
Modify the AndroidManifest.xm1 to include the <uses-permission . ... USE FINGERPRINT>.
Declare the application must be installed in external storage.
Install the application in internal storage.
Set the targetSdkVersion to a version that has the permission available to fix the issue.
Update the targetSdkVersion to the most recent version.


38. An Android telephone directory application built to keep the directory in memory reduires the ability to query the device installed on and determine the amount of heap space available for the application. Making a call to which of the following will programmatically query the device to obtain this information?
AndroidManager.getAppInfo
MemoryManager.getAvailableMem
AppManager.getAppInfo
ActivityManager.getMemoryInfo
SystemManager.getAvailMem



39. Which of the following class definitions implement the interface shown below in Android?
interface MInterface {
var varl: String var var2: Int fun method1 ()
fun method2 () = "Hello there”}



40. A company has received complaints about the Google Play photo-taking application installation on devices without a camera and then crashing when the application tries to use the camera. Which of the following must be performed to prevent customers from seeing errors in Android?
Add code to the Android Manifest: <uses-feature android: name="android.hardware.camera"
required-"true" />
Add code to the Android Manifest: <uses-permission android: name-"android.permission .CAMERA" />
Add the code below to the Android Manifest: <uses-permission android:name="android.permission.WRITE EXTERNAL STORAGE" />
Create a foreground service to ensure the camera code is always accessible to monitor hardware availability.
Modify the application code where the camera is used to catch the exception causing the crash and inform the user.



41. An application encounters an IllegalArgumentException stating a fragment is unknown to the NavCont roller. After eliminating implementation errors, the fragment is still unknown. Which of the following issues cause this error in Android?
The Gradle cache needs to be cleared and reset.
The navigation graph has become corrupted and requires reinitialization.
The application build has experienced problems and must be redone.
The value of currentDestination is invalid and requires update.
The NavController has already moved on to the next location, so the current location must be verified.    42. An Android application AppActivity extends FragmentActivity and overrides onSaveInstanceState () . During compilation, the developer sees an error stating the compiler will not access android. lifecycle. LifecycleOwner. Which of the following techniques will resolve this error?
Shut the IDE down, delete the build.gradle files, and restart the IDE.
Ensure the Grade dependencies include implementation 'android. lifecycle: lifecycle-extensions:2.2.01.
Update to the latest core-ktx library version.
Include a classpath "org. jetbrains. kotlin: kotlin-gradle-plugin: 1.5.20" entry in the Gradle dependencies list.
Ensure the list of repositories in the settings.gradle file includes jcenter () so updates are made.



43. An Android application must ensure the audio files created by the application and stored on a directory on the external SD card are unable to be read by applications looking for file content via the MediaStore content provider. Which of the following actions accomplish this?
Set the owner of each file to be the system.
Remove the entries from the MediaStore. Audio table.
Include an empty file named ". nomedia" in the directory with the files.
Add each directory to be marked private in the AndroidManifest. xml.
In the Activity creating files, call Application. ignoreMediaFiles (String location) in the onCreate () method for each location to be ignored.



44. An Activity creates a SharedPreference instance which is not accessible to other applications or other in-application activities. Which of the following method calls are used to accomplish this in an Android application?
getCommonPreferences ("activity", Context. MODE APPEND, VISIBLE. FALSE)
getPreferences (Context.MODE PRIVATE)
getPrivatePreferences ("mypref", Context.MODE PRIVATE)
getSharedPreferences ("mypref", Context.MODE PRIVATE, VISIBLE. FALSE) getSharedPreferences ("mpref", Context MODE PUBLIC, VISIBLE. FALSE)



45. Testing on a real device errors out without cause. The application works without error during testing with an emulator. Which of the following reasons will cause the unexpected behavior in Android?
The test is timing out on the real device because the device lacks resources.
The real device has configuration issues not accounted for by the emulator.
A device update or other real world configuration change is causing the application to fail.
The real device has a low battery, which is causing the application test to fail.
The application is using a different version of a library or other resource on the real device than on the emulator.



46. Which of the following enable a developer to show a camera preview in an Android application?
Send the CAMERA IMAGE CAPTURE Intent, decode the returned data and map to a visible ImageView.
Capture the raw incoming data stream and render to a BitMap which is assigned to an ImageView.
Use a CameraSurfacePreview.
Use a CameraPreview.
• Use a SurfaceView.



47. Which of the following components are part of the Linux kernel portion of the Android architecture?
Window Manager
Audio Hardware Abstraction Layer (HAL)
Camera driver
Search Service
AudioFlinger    48. The code below shows the creation of a Notification Channel for use in an Android Lollipop application. The code shows the publishing of a Notification using a channel. Which of the following describe an error in the code and a valid solution for the problem?
final String ID = "example";
final String NAME
=
"my name";
NotificationManager manager = (NotificationManager)
context.getSystemService (Context.NOTIFICATION SERVICE);
//Create channel
NotificationChannel channel =
new
NotificationChanne1 (ID, NAME,
channel.setDescription ("description");
NotificationManager. IMPORTANCE_ DEFAULT);
//Build and show notification
Notification n = new NotificationCompat. Builder (this, ID)
•••
.build () ;
manager. notify (123, n);   49. An Android application has requested location updates from the Fused Location Provider using a long. running synchronized operation. The callbacks invoking the long-running operation begin to back up, to the point where the callback will time out. Which of the following changes will keep the callbacks from timing out while maintaining the application's functionality?
When a location update is received, set the update interval to match the requested interval of 7500ms to reduce the number of incoming updates during the execution of the long-running operation.
Use setFastestInterval (1000) to accept location updates over the set Interval () value.
Remove the synchronized keyword from the function which contains the long-running operation.
Use the Fused Location Provider's get Last Location function on a timer of 7500ms.
Set the request priority to LocationRequest. PRIORITY_ LOW POWER when the long-running operation is in progress.
