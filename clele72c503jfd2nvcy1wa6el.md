# Improving Android App Performance

When it comes to app success no one can deny the factor of app performance. It doesn't matter if your app has smooth animations, transitions, appealing images, features, etc…none of them matter if app performance lags. It matters as a second priority first performance is always how app performance. App performance metrics are always to be considered to bring a better user experience. Many bottlenecks cause **bad performance**, the developers need to consider, like:

*   **Size**

When it comes to size always every one prefers a small-sized APK which saves extra space for their phone. It is obvious as a user that we choose a 10 MB space-consuming app than a 100 MB which offers the same functionality. Not only 4G or 5G does exist for everyone even still 2G and 3G are also to be considered in the big picture to promote more downloads.

*   **Launch time**

Do you wait for an app to launch for more than 5 seconds? Usually, we will not think for any other seconds to uninstall faster than the time taken to download or report in the app store and give a 1-star rating.

*   **Speed**

A poor speed always affects the app. Speed is measured by the app response time, loading of contents, etc… App with poor speed performance is mostly nicknamed to be the worst app.

*   **Size of images and video**

Images and videos with low quality distort the app. The images with the usage of JPEG, and PNG format usually are not fit for all sizes of screens creating images for each screen makes the app size bigger. In the case of videos when the user has the least bandwidth and seeing buffering is the expected result.

*   **Screen Resolutions**

There are so many devices like mobiles, tab, smart tv, and wearable of various shapes and sizes. App with poorly managed in size and orientation creates buzz. So there are some situations the layout designed will not work the same on all device sizes. Some apps will provide a great experience on one mobile and if the app doesn't give the same effect while using different mobile. Poor designs usually affect speeds creating slow app performances.

*   **Memory usage**

To do multitasking for users Android sets limits on RAM usage for apps. Although the given limits are not static they will always change according to the mobile usage by each app. If the apps are still running in the background unnecessarily and use memory always and are not freed up creates a problem called a ***memory leak.*** *Developers giving less importance to memory leaks leads to the drain of battery life.*

*   **Poor Networking**

Heavy usage of data and WiFi consumes a lot of battery causing power drain. Today every app relies on networks either in case of getting media or connecting with cloud service, backend networks are needed. Lots of network traffic are used to achieve the desired result in the app which directly leads to battery consumption and sometimes the app will not adjust according to your network connectivity like 2G, 3G, 4G, and 5G.

The primary goal while considering networking is a faster response with less battery consumption.

*   **Offline model**

Users will get irritated if it is an app is not properly managed in offline mode also. It creates a horrible user experience without proper **caching** which affects the app performance. There will be also a consideration for the offline state also. Users prefer a smooth transition when there is a sudden network change from offline to online state and always prefer sync when it becomes online. So it prefers to save basic data in local storage and it will not affect it while going through online. For example, if an app is online and the user is editing sudden network change led to offline a good app always offers to edit offline and save locally and when the network regains all the editing changes should be visible online. Either than repeatedly doing everything once again from scratch it is preferred to use an offline model.

### Good ways to improve app performance

Can a developer figure out and solve it? The straight answer is yes. Making 1 app with a good feel user experience is equivalent to making 100 similar apps. So, giving extra time to tackle it is always better.

### **1\. Reduce app size**

Reducing the app size mainly includes *two processes the* first thing is to *analyze* the size of an app like how much space is utilized by it. The second thing is to *take steps to reduce the size* sometimes size increases because of code, and images likewise so let's take a look into solutions to shrink app size.

### ***1.1 Analyze***

### ***App size (APK Analyzer)***

*   Using Analyze APK option

Android studio has a default option to analyze the APK. To do this go to

Build > Analyze APK > dialog box opens > select your APK(ProjetcName.apk) 

You will get a report of your app with information including the name of APK, files in your app like manifest, res, etc, and details of downloadable size likewise. If your app is for production and planning for updating with versions you can also compare your current version with the previous one.

*   Profile or Debug APK option

Android Studio also has another method in the file section you can navigate in the following order

File > Profile or Debug APK > Dialog box opens > select your app APK file > OK

A similar report will you get as I said above with pieces of information like downloadable size, res file, etc…

### Monitor CPU, Memory, Network, and Battery (Android Profiler)

Android Studio has Android Profiler to monitor the CPU, memory, network, and battery used by the android app. To open it follow the instructions

View > Tool Window > Profiler > Dialog box opens > select device which you want to profile your app performance (Emulator, or your mobile using USB Debugging)

By doing so you can see all the particular reports depicting the CPU, memory, battery, and network usage of your app on the selected device. So by monitoring it you will get clarity on whether your app is using its minimal or not.

### ***1.2 Improve performance- Take necessary actions***

So by analyzing we get an idea of where is the size of the app increases. So we can take the steps mentioned below to reduce app size

*   **Upload app with App Bundles(.aab)**

App Bundle is a publishing format. From August 2021 apps are required to publish in App Bundle format in Google Playstore. The format includes all your app code and resources. The APK generation and signing to Google Play are postponed in this format. App bundle is used to generate and serve optimized APK for each user's device configuration. So they download only the code and resources that are needed to run your app which results in a smaller app size. So we don't need to build, sign and maintain separate APK for different device configurations.

*   **Remove unused Resources (Proguard, R8\[Gradle 3.4.0 and higher\])**

To make the app size small it is a must to shrink your code by doing it all unused resources and code will be removed.

Proguard and R8 help to shrink the code. But now R8 is commonly used before the release of Gradle 3.4.0 Proguard has been used but now R8 comes to the big picture to shrink. What all things does it shrinks:

1 Code  
2 Resource  
3 Shortening class and members name  
4 optimize code by rewriting 

> Use R8 for all release builds

*   **Compress PNG and JPEG files**

If your app really wanted to use images in format PNG or JPEG always compress them without losing the image quality by using appropriate online or offline tools you prefer some of the tools you can use is

[https://pngquant.org/](https://pngquant.org/)

[https://github.com/google/zopfli](https://github.com/google/zopfli)

*   **Use WebP or SVG type**

It is recommended that *WebP* is the best format for images in android because it supports both lossless(PNG) and lossy (JPEG) compression. WebP is fully supported on web browsers and is considered safer on Android.

SVG is a vector graphic format supported by the web browser. It is ideal for logos, illustrations, and other graphics which can scale without losing quality.

*   **Use Vector Drawable for images, icons, and animated images**

Vector graphics can be used to create icons, images, and animated images which make shrink in android app size. In Android Studio there is an option to create your media in a vector object which is represented as ***VectorDrawable.***

*   **Minimize the usage of external libraries**

While building an app to add external features we include external libraries. But when using it we avoid that fact like some of the class or members are not required for your application. When external libraries have referred the classes associated with them are also called and some of them are not actually required which eventually increases app size by consuming space that is not needed for the app.

So it is preferred to use libraries provided by Google and well-maintained libraries.

### 2\. Decreasing App launch time

When it comes to launching time the average top lunchtime on Google PlayStore is between 800ms to 4.5s. So definitely more users prefer launch time between 800ms to 4.5s and less. How can we launch our app faster?

*   Don’t use too many views on the launch screen
*   Don’t initialize code in the app object
*   Use garbage collection as possible
*   Avoid using UI that is not required for the initial screen
*   Use the Firebase performance monitor to check the launch time

### 3\. Optimizing Screen Resolution

There is not only a mobile screen with only one screen size. The layout structure should be different for small to big size screens. So while creating an app always remember

*   Design layout in a way that it can be accessible on portrait, landscape, large, or small-size screens.
*   Optimize for different screen densities MDPI and HDPI
*   Implement bitmaps to scale with views
*   Modularize fragments
*   Build alternative layouts
*   Check with different android emulators to confirm that it is complementing different screen resolutions.

### 4\. Improve memory usage

When it comes to memory developers also need to consider the memory leaks associated with it. Sometimes developers only focus on features and avoid factors like memory usage of the app. Memory leaks should also be taken care of for better performance. Poorly handled memory leaks led to unpleasant app performance.

> Memory leaks are caused when unused objects occupy unnecessary space in memory. The unused spaces are still referred and not freed by Garbage collector

How to solve it

*   Use LeakCanary or Android Profiler to detect memory leaks
*   Release UI resources when users move to different UI
*   Write memory-efficient codes
*   Minimize usage of the third-party library
*   Choose static inner class
*   Unregister listeners and events
*   Make yourself understand with architecture using
*   Don't use a static reference
*   Review your code

### 5\. Optimize network usage

Consuming more data in your app drains more battery power. Getting the best networking performance in an app requires optimizing its usage. Most of the app use networks for loading images, making API calls, etc so optimizing it in a to way to minimize battery usage is the best solution for it.

How to achieve it

*   Load text first and images second
*   For images use libraries like Picasso, Glide
*   Cache data and resources
*   Use Jetpack WorkManager to sync and load data that your app needs and used later when the user is off the application.
*   Design an efficient API that has reduced workloads and consistency.

### 6\. Cache Whenever possible — Configure the Offline model

Sometimes the app may affect by a bad network connection and hinder the user experience app should be able to display information offline. Caching comes as the main frame of topic in the offline model because when a user loses network connection, caching helps the user use the app even offline and make a smooth transition when the network is connected.

How to make this possible

*   Make a few HTTP requests
*   Store data offline which helps to access data offline by storing it in a local server or browser where the device can access it.
*   Making to edit offline and sync online
*   The text should load first and the image second
*   Use image caching

### Conclusion

App performance is a vital part of app development sometimes we lack in the area leads to poor user experience. Giving a certain amount of time to figure out and rectify it requires some effort. But to achieve a good outcome additional effort should also be taken.

Do you also feel your app also needs improvements before launching? So what’s your thought about it?

Happy coding hours………….👋👋👋👋👋👋👋