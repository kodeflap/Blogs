# How to Simplify Android Documentation with Dokka and KDoc

All good products will include an instruction manual to make it easier for users to use the product. A product that is easy to use can make a big difference. This also applies to writing any software. For developers, understanding code has a huge impact on creating user-friendly applications with correct functionality.

In this blog post, you can see how to use Dokka and KDoc to simplify your Android documentation and make it easier for other developers to work with your code. We will walk through the basics and show you how to use them to create well-organized and easy-to-use Android documentation.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677416047573/362f91a1-8160-41e4-9536-2b1921948aee.png)

Workflow of dokka \[made with [canva](https://www.canva.com/)\]

### What is code documentation?

Code documentation is the description that helps to understand what each code does in the application. For instance, it helps to give a clear overview of what each variable does, what a particular function is in the project, whether it has a parameter or any return type, and what its impact is in the code like details are being documented well.

### Why should we document code?

Imagine you have the opportunity to work on a large project with millions of pieces of code. You are responsible for correcting errors in this section. You find the line of code where the error occurred and the error was caused by the two functions being called, then you navigate to that function code after going through each line of code you discover that an access modifier is causing the problem. As a result, the developer has to go through a lot of code, and they all have to understand the interrelationships between the codes to tackle a problem. Handling an error in a bigger project in this way is clearly a headache for developers, especially for a newbie.

This is where good documentation helps. Code documentation is usually used to **understand what variables, classes, objects, functions, etc.. are used in the application and what is its purpose and give information about does it have any parameters, receiver, or does it have external links.**

If you get enough info about the code it is easy to work in code which eventually led to a **decrease in the amount of time spent on solving and implementing a solution in the application.**

But always there are **two worst-case scenarios while documenting**

#### Lazy documentation

Lazy documentation is the document with the least information provided. If a document is not giving you enough information about functionalities it is lazily formatted. Which is good for nothing, because it doesn’t bring any value to make you understand the code.

#### OverInfo Documentation

Some documentation gives information more than what it needs resulting in uncleared usage of code and makes confusion about the code. Spending a fruitful time reading out documentation is important to understand the proper usage of code but what if it takes double effort to understand the code? or information overloading creates too much difficulty in processing the code for a developer or even led to uncleared usage, this happens in over info documentation

### Good documentation characteristics

*   Should be understandable
*   It should be accurate and up to date
*   Simple and concise
*   Proper formatting
*   The document should always hit the target
*   Should properly describe each functionality
*   It should properly document its parameters, links, receivers if any

### What are KDoc and Dokka?

In Java, Javadoc is used to document java code. Before Dokka, there is no proper tool to document Kotlin. Dokka is a documentation tool that is similar to Javadoc. The main difference between Javadoc and Dokka is that Dokka supports documentation of both Kotlin and Java. Dokka the documentation is made possible with KDoc.

#### KDoc

KDoc is the **language** used to document Kotlin code. To generate good documentation proper commenting is needed, to do this KDoc helps to commend using block tags and markdown. It is basically a plugin used in Android studio which helps to document. We can use KDoc by the following

*   KDoc commenting started using / \*\* as the opening tag and ended using the \*/ closing tag
*   KDoc supports block tags and inline and HTML markdown to provide additional information about the elements which is embedded using @ symbol

***Block tags***

*   @receiver: document receiver extension
*   @param: documents properties of class or functions with name and description
*   @see: documents link to a specified class or function

***Inline Markdown***

*   \# h1, ## h2, \[\], > etc.. tags are supported

***HTML tags***

<i>, <img>, <html>, <head> etc.. tags can also be used

> Read more about [markdown guides](https://www.markdownguide.org/basic-syntax/) to get familiar

#### Dokka

It is a tool used in to generate documentation. The generated documentation can be **viewed basically in formats that include HTML, markup, and standard Javadoc**. Dokka supports documentation of both java and Kotlin. It generates a Kotlin document if it is embedded using KDoc in the Kotlin file and generates Javadoc if commented using Javadoc comments.

### How to implement

#### 1\. Implement dependencies in project-level build.gradle

plugins { id ‘org.jetbrains.dokka’ version ‘1.7.0’ apply false}

#### 2\. Implement dependencies in module-level build.gradle

plugins { id 'org.jetbrains.dokka' }

*   If you have multiple modules add in there too
*   Sync project

After a successful build do the following steps

#### 3\. Document Generation

Open the **terminal** option in Android Studio and type the following

*   To generate a document for the **module** type the script in terminal

./gradlew dokkaHtml

*   To generate a document for **multi-module** type as follows

./gradlew dokkaHtmlMultiModule

Once it completes the process you can see the generated document in **build/dokka by changing the view type from Android to Project.** Here is a sample dokka build generated in open source project [**Sliderz**](https://github.com/kodeflap/Sliderz)**.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677416049109/f453d823-7a10-4582-b822-bf98b49ff4ca.png)

Project view of [sliderz](https://github.com/kodeflap/Sliderz)

And by clicking the index.html and opening the browser we can see the code documentation generate in **HTML** format which is the **default format.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677416050224/09524739-608d-4dcf-9844-6fad86e99aed.png)

Code documentatio[n of sl](https://github.com/kodeflap/Sliderz)iderz

> The Dokka also supports other formats including Javadoc, gfm, and Jekyll.

But if we have not included any Kdoc commenting then it will give a blank HTML document. To do so we have to include KDoc comment. The normal commenting using // comment, /\* comment\*/, <!-comment → are not regarded as Kdoc comments. We can do Kdoc commenting using the below symbol.

#### Kdoc Commenting

/\*\* and press enter  
\*\*/  
fun foo(parameter){ }

#### Remainder

*   More explanatory code documentation only happens by choosing suitable naming conventional and clearly defined variable names.
*   You can provide additional details to be displayed in the documentation

### Sample Kdoc commenting example

> /\*\*  
>  \* Performs a complicated operation.  
>  \*  
>  \* [@param](http://twitter.com/param "Twitter profile for @param") remote If true, executes operation remotely   
>  \* [@return](http://twitter.com/return "Twitter profile for @return") The result of executing the operation   
>  \*  
>  \*/  
> fun foo(remote: Boolean): Result { … }

It can be further expanded if it has a constructor, exception throwing, etc.. are implemented in code.

You can look at the further Block Tags used in the official KDoc documentation.

[https://kotlinlang.org/docs/kotlin-doc.html#module-and-package-documentation](https://kotlinlang.org/docs/kotlin-doc.html#module-and-package-documentation)

This is a quick guide for implementing Dokka in the android studio. You can check the further syntax in the above link.

This whole blog is about basic information about documentation. Hope you enjoyed it and helpful in your development journey. That’s all for today.

Have a nice day 👋👋👋👋