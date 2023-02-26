# Android library compatibility and public API management with Binary Compatibility Validator

Android library compatibility is a major concern for developers, as it affects the performance and stability of the applications they create. It is essential to ensure that the libraries used are compatible with the Android platform, so as to ensure a smooth and successful user experience.

Developers typically use internally built and third-party libraries to create applications. During upgrades or when different versions are employed, we may experience deprecation, crashing, exceptions, and other compatibility issues. It’s expected that when a client uses your library, it’s meant to be long-term and fulfill their needs. A library is more than just reusable code, functions, or pre-assembled routines. It must also be taken into account in terms of compatibility, amount of space it uses, and memory consumption.

### What is **library compatibility?**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677416036900/b47210f8-a1ef-42dc-a76e-abaecd32e773.png)

Library compatibility \[made with [canva](https://www.canva.com/)\]

A library is said to be compatible if it does not affect the normal operation and functionality of an application when another version of that same Library is substituted in its place.

Take a look at the image above; the code makes use of libraryA which has different versions like v1.0.0, v1.0.1, v1.1.1, and the current version v2.0.0. The code is unaffected by an upgrade, therefore libraryA is normally compatible. More specifically, you can specify library compatibility as follows;

#### 1\. Backward Compatibility

*Updating a library doesn’t break the software, it’s compatible with older versions* then the library is said to be backward compatible. Based on the image above, we can say that v2.0.0 is backward compatible with v1.1.1 as replacing it does not cause errors.

#### 2\. Forward Compatibility

Just as if we were to *switch or replace a newer version with an older one*, it is forward compatible. In the example above; if changing v2.0.0 to v1.1.1, doesn’t disrupt the flow then it is said to be forward compatible. So v1.1.1 is said to be forward-compatible.

### Source Compatibility and Binary Compatibility

While maintaining libraries we should also know these two types of compatibility. As most of the compatibility is expressed in terms of backward compatibility the below explanation is based on backward compatibility.

#### Source Compatibility (API- Application Programming Interface Compatibility)

In software libraries, the API serves as an interface that describes how applications can interact with the libraries. The **API is expressed as the source code itself**, which usually consists of data types, functions, constants, various classes, etc. which can be used to access the feature. A library is **API/source compatible,** means that changes made in different versions of the library are functionally identical.

#### Binary Compatibility (ABI- Application Binary Interface Compatibility)

Before talking about binary compatibility, let’s look at the Android build process for changing code written in Java or Kotlin to bytecode for this concept.  
Below is the Android build process, from code written in Java/Kotlin to running the app.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677416038531/dd1c8c13-889b-4414-add5-06cbc498ad1e.png)

Android compilation process\[made with [canva](https://www.canva.com/)\]

**Binary compatibility** is expressed in terms of ABI. ABI usually has bytecode (.class) compiled by the JVM process. If the **bytecode** compiled by the different versions of the library can be swapped without causing **linkage errors** (an error occurs when the compiled bytecode cannot resolve references at runtime), then it is said to be ABI/Binary compatible

### Version Scheme in Library

A Library version number is defined in terms of the above concepts. The library versioning contains components like

*   **Major — Based on Binary / ABI Compatibility.**

Changes to major version numbers are used to indicate major version changes, such as the removal and addition of parameters, functions, name changes, etc. that could ***result in an incompatible change to the API or ABI*.**

*   **Minor — Based on Source / API Compatibility**

Changes in the minor number indicate additional functionality has been added like adding a new function or new fields without changing the functionality of the existing version. But it can ***also lead to ABI incompatibility.***

*   **Patch — Based on Compatibility**

Indicates that some bug fixes have been made without making any major changes to the major and minor sections like modifying the field rules

### Binary Compatibility Validator Plugin- Public API management tool

Braking Binary Compactibility means breaking the entire ecosystem. It leads to the crashy functionality of the app. [Binary Compatibility Validator](https://github.com/Kotlin/binary-compatibility-validator) is a tool that helps developers quickly and accurately assess the compatibility of Android libraries and public APIs, allowing them to ensure that their apps are running as expected. The Binary Compatibility Validator can also be used to test any changes made to an Android library or public API, making sure that their apps are not adversely affected by the changes. With this tool, developers can simplify the compatibility testing process and give their users the best experience possible.

The Binary Compatibility Validator transforms the bytecode (.class) generated from the Android compilation JVM process from one or more source codes to form a public API based on Kotlin visibilities and manages the public API by checking if there is an incompatibility binary.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677416039905/00b0c427-5467-48f8-bea3-75c09bbf93c1.png)

Binary compatibility validator workflow \[made with [canva](https://www.canva.com/)\]

### Steps to include **the binary** compatibility validator

#### 1 . Add gradle dependency at the *Project level*

 plugins {  
  
    id 'org.jetbrains.kotlinx.binary-compatibility-validator' version '0.12.1' apply false  
}

You can specify additional things in the apiValidation block inside the *App level gradle* like

*   packages, projects, classes — unused classes, documentation, packages, and submodules that you don't want to include in Public Apis are specified here.
*   nonPublicMarker — Set of annotations (kinds of @InternalApi- for private API) that you want to exclude from public API.
*   ValidationDisabled — A binary flag to enable and disable compatibility validation

apiValidation {  
  
    ignoredPackages.add("com/example/myapplication/ui/theme")  
    ignoredClasses.add("com/example/myapplication/BuildConfig")  
    ignoredProjects += \["example3", "subproject2"\]  
    nonPublicMarkers.add("my.package.MyInternalApiAnnotation")  
    validationDisabled = false  
}

#### 2 . Perform tasks

After completing the above steps, the second step is to run the first task. In the Binary Compatibility Validator plugin, there are mainly 2 tasks, **apiDumb, and apiCheck**, which need to be executed. I will explain its usage with an example.

#### \* How it works

For sample, I created a kotlin library that returns the square of a number and internal fun which is annotated with @PublishedApi

sample v1.0

fun square(x: Int): Int{  
    return x \* x  
}  
  
@PublishedApi  
internal fun sample2() {  
   val num: Double = 3.16  
}

In the terminal section perform the first task

#### — apiDumb(First task)

path > ./gradlew apiDump

After the above command is executed successfully, an API with **.api** extension (sample.api) will be automatically created in the **api folder.** Verify by switching to the project view and checking the module/app section where you implemented the binary compatibility validator. When expanding there will be an additional api subfolder with a .api extension file

See the sample.api generated by running the above command

public final class com/example/myapplication/MainActivityKt {  
 public static final fun sample2 ()V  
 public static final fun square (I)I  
}

> *As we ignored additional classes, packages, classes, and annotations in the apiValidation the generated api contains only the function declared in MainActivity class like sample2() and square()*

#### \* Overview of Public API

The Public API contains classes and members that are declared. Not every class and member is included in the Public API. It includes

***— Class* that are public in terms of**

*   Public or protected JVM access
*   Classes that have visibility like public, protected, internal(should be annotated with publishedApi), and no visibility.
*   The class which isn’t local, a synthetic class with mappings
*   The class should contain at least one effective public member
*   If the class is a member of another class, it is should be a public class
*   If the class is a protected member in another class, it should be contained in the non-final class

— **Members which are public in terms of**

*   Public or protected JVM access
*   Members should have visibilities like public, protected, internal(@publishedApi), or no visibility.
*   If the member is protected, it should be in a non-final class
*   Members should not be synthetic access method for a private field

After looking at the Public API we are going to understand the importance of the second task of the plugin by making some changes by adding an interface, changing a method name, and implementing it in MainActivity.kt

sample v2.0

//Added new interface sample  
interface Sample {   
    var hello: String  
    fun print()  
}  
//Changed name of function sample2() to sample()  
  
@PublishedApi  
internal fun sample() {  
   val num: Double = 3.16  
}  
//implemted interface in mainActivity Class  
class MainActivity(override var hello: String) : Sample {  
    override fun print() {  
        TODO("Not yet implemented")  
    }  
}

Now run the below command in the terminal

#### — **apiCheck(Second Task)**

path > ./gradlew apiCheck

So running this command will compare the public API in the api subfolder and verify the build by entering to verify pipeline. If it doesn’t cause any binary mismatch then the task will be successful.

In this example, the task will fail because of breaking the binary compatibility. So it will produce an unsuccessful build with the exception

path> ./gradlew apiCheck  
\> Task :app:compileReleaseKotlin  
w: path\\com\\example\\myapplication\\MainActivity.kt: (10, 8): Variable 'num' is never used  
\> Task :app:apiCheck FAILED  
FAILURE: Build failed with an exception.  
\* What went wrong:  
Execution failed for task ':app:apiCheck'.  
\> API check failed for project app.  
 - - D:\\MyApplication\\app\\api\\app.api  
 +++ D:\\MyApplication\\app\\build\\api\\app.api  
 @@ -1,6 +1,20 @@  
 +public final class com/example/myapplication/MainActivity : com/example/myapplication/Sample {  
 + public static final field $stable I  
 + public fun <init> (Ljava/lang/String;)V  
 + public fun getHello ()Ljava/lang/String;  
 + public fun print ()V  
 + public fun setHello (Ljava/lang/String;)V  
 +}  
 +  
 public final class com/example/myapplication/MainActivityKt {  
 - public static final fun sample2 ()V  
 + public static final fun sample ()V  
 public static final fun square (I)I  
 }  
+public abstract interface class com/example/myapplication/Sample {  
 + public abstract fun getHello ()Ljava/lang/String;  
 + public abstract fun print ()V  
 + public abstract fun setHello (Ljava/lang/String;)V  
 +}  
+  
You can run :app:apiDump task to overwrite API declarations

So to fix this we should execute the first task (apiDumb) one more time which will produce a new Public Api.

path > ./gradlew apiDump

public final class com/example/myapplication/MainActivity : com/example/myapplication/Sample {  
   public static final field $stable I  
   public fun <init> (Ljava/lang/String;)V  
   public fun getHello ()Ljava/lang/String;  
   public fun print ()V  
   public fun setHello (Ljava/lang/String;)V  
}  
  
public final class com/example/myapplication/MainActivityKt {  
   public static final fun sample ()V  
   public static final fun square (I)I  
}  
  
public abstract interface class com/example/myapplication/Sample {  
   public abstract fun getHello ()Ljava/lang/String;  
   public abstract fun print ()V  
   public abstract fun setHello (Ljava/lang/String;)V  
}

The Android Library Compatibility and Public API management process can be a daunting task for Android developers. With the use of a Binary Compatibility Validator, the process can be made much easier.

This article is all about android library compatibility and how to manage binary incompatibility with the ***binary compatibility validator plugin*** to ensure that the libraries used are compatible with the Android platform for smooth app performance. I hope this article is useful for you.

Thank you for reading the article.