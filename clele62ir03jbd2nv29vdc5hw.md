# Structuring a Clean Architecture for Note App in Android Studio

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677415976375/99780e8a-48b8-4829-a24b-3e83594397e1.png)

MyNotes

In this blog post, you will be guided on making a note-taking android application in Kotlin. You will learn the overall architecture used for this project, and how to structure the project.

Before going to the overall architecture it is recommended to fork the [MyNotes](https://github.com/kodeflap/MyNotes) project and then clone it android studio

If you build and run the project it will look like this

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677415978128/dee6f44b-1248-4ffb-8e2c-f69a1a0e7020.png)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677415979430/ab1e0a62-0b7b-4f54-a609-dd3c1aad2f9e.png)

### About Architecture

Clean architecture is a way to organize the code in the form of layers. The inner layer should not be dependent on the outer layer. For example, if we change our database to another database engine it will not affect the presentation layer and the same applies if we change anything in the presentation layer there should be no effect in the data layer.

> The domain layer should be independent of libraries(can have [standard kotlin libraries](http://kotlin%20standard%20library))or frameworks

The below figure represents the clean architecture

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677415980996/23caa566-fbfd-4f8b-a9fe-916a6548978e.png)

*   Inner circles like entities(Enterprise logic) and use cases (application business rules) should contain business logic
*   Outer layers consist of implementation details

### Advantage

1.  Clear separation between UI and Data layers so it avoids cohesion
2.  Easy to test
3.  Can implement new features easily

### Package Structuring of Note app

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677415982042/13dd8943-1772-4e36-8df6-ca02bdc2f918.png)

Package structure

1.  **di:** Dependency Injection related files are placed in it.
2.  **feature\_note:** It is the single feature now included. If you want to include another feature repeat the same packaging structure for other features like this that consist of data, domain, and presentation package. So if you think why the answer is pretty straight forward it can be easily understandable if your project is very large you don't want to scroll through many pages and search for what just goes to the feature and can access all related domains, data, and presentations for a particular feature.

2.1 **data:** Package contain all related files and packages related to data sources

2.2 **domain:** The domain consists of business logic related to the feature which is related to the app that handles the exchange of information between data and the UI or presentation layer. The domain layer includes the model, repository, and use cases.

2.3 **presentation:** This layer handles the UI part

3\. **NoteApp:** This is the root class for injecting dependencies

So we can check how it implemented in the app

### How To arrange

Single Module app currently one feature\_note is provided in that we create the layers like.

### 1 Data Layer

The data layer has a data source that contains the Dao class file for Room Database which contains a function to do CRUD operations and then the **class that extends from Room Database**

then implemented **NoteRepository implementation** class that extends from the domain layer NoteRepository which includes all the methods to get notes, insert and delete the note. Here it uses a Flow to return a list of notes.

Like this other operations like delete, and insert functions are created. Next, we can move to the domain section.

### 2 Domain Layer

The domain layer has a **model class** that consists of title, content, timestamp, color variables used for the app.

next consists of the **interface NoteRepository** which will be serving as a fake version to serve use cases to make more separation.

Next serve **uses cases** in here our use cases are ADD, DELETE, GET, UPDATE and make a data class for view models

### 3 Presentation Layer

In the presentation layer arrange the code in a manner by separation of functionality notes home screen and notes screen which is used to for doing CRUD operation based on these 2 composable arrange the package in a way **composable** which is used to design the text field, the screen of the page second it should contain **ViewModels, Event, and state**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677415982988/f8457fdc-651d-42d0-9f79-91c4d2cb0dcc.png)

Composable only place items that we use to design using Jetpack compose. View Model should inject from the constructor that uses use cases and extend from ViewModel() also place the code for the event and state change behaviors in it.

It should also contain an **entry point activity** which is annotated as @AndroidEntryPoint where we load all the UI themes and navigation-related items.

Additional following things should also be noted if you are building the app

### Root Activity

The root activity should be annotated as follows which became the root class for injecting dependencies

### Dependency Injection

If your app is using dependency injection separate the arrangement by giving a separate package for doing dependency injection in the application. Here the app uses Dagger Hilt so a separate package was made to make all dependency injection-related files.

### Util

This package contains all the additional items related to the projects like name, variable name, strings, etc…

This article is all about giving a glimpse of a practical example of clean architecture. How to structure your project to make it a clean architecture.Hope you get an idea.

The project provided is a sample example of clean architecture you can refer to and can understand the structuring of the application. As the app is made to open source if you can fork it, any additional contributions are also welcome if you find any doubt you can discuss it there.

[**GitHub - kodeflap/MyNotes: 📓My notes is for organizing your notes.**  
*My Notes is an app that helps you to keep your base notes. You can insert, update and delete note as you wish. The…*github.com](https://github.com/kodeflap/MyNotes "https://github.com/kodeflap/MyNotes")[](https://github.com/kodeflap/MyNotes)

So have a great day 👋👋👋👋