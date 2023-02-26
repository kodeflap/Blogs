# Introduction to APIs

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677416066841/eafebc34-28fd-45df-9704-04e1765ba4da.png)

We use different applications in our day to day basis. Many apps include shopping apps(Amazon, Flipkart, etc…), entertainment apps (Netflix, Disney, etc,…), Games, social media, and many more. Many applications that we use include different sign-in methods like Google, Email, and Facebook and many apps integrated other services, for example, some apps include a payment gateway like Paytm, Google Pay, etc... for smooth functioning even when using weather applications we are using API. APIs are included in most applications nowadays.

### What is an API?

An API is an acronym for **Application Programming Interface**. The application mostly needed the internet for smooth functioning which works with APIs. They cannot work in offline mode.

An example of API implementation is, using an app with the sign-in with Google option. What happens when we click the sing-in with Google option and type our name and password? Here comes the action of API. The API will help to take the login request to a server then the server checks the request and take the required action and pass it to API the API then carries this response to the application if you are already a member you will be redirected to the app either wise it give you response to sign-up.

A common scenario for understanding API is the restaurant food ordering process. First, you(***Application/EndUser*)** go to the restaurant and choose a table.What happens next? the waiter(***API***) appears to place your order(***Request***) the waiter takes the order and reaches out to the kitchen then the chef prepares the food(***Response***) and the waiter takes the food to you. This is what will happen in the case of APIs workflow.

So from these, we can arrive at a basic conclusion about APIs:

*   It serves as a middleware that allows two or more applications to communicate with each other.
*   APIs can be used to define requests, handle business logic and manage data formats that should be used and conventions to adhere to when building software products.

### Types of APIs

There are 4 types of APIs

1.  Public
2.  Partner
3.  Private
4.  External

### Public

*   *In* ***Open APIs/ Public APIs*** there is no restriction to access these APIs.
*   Involves moderate authentication and authorization.
*   Some companies also impose per-call costs for using their provided public APIs.

### Partner

*   Developers need specific rights and licenses to use the APIs*.*
*   Require stronger authentication, authorization, and security.
*   This APIs charge a fee for using their services.

### Private

*   *Also known as* ***Internal API*s**.
*   Usually designed for internal use within the company.
*   Used among internal teams in the company to improve their products and services.
*   It has weak security and authentication or none at all because it is used internally in the organization.

### External

*   These APIs are accessed by third parties that are external to the organization.
*   They are mostly designed by considering the end-users.
*   They often make organizations' data and data accessible on a self-service basis by developers around the world who are looking to create a new application by integrating these APIs. Example: Google Maps API that is used by traveling, and food delivery apps.

### Why do we need APIs?

Some of the common benefits are:

*   **Efficient**

Reduce the amount of work as it was created and hosted by a third party. As a result of this, the application development process will be faster.

*   **Security**

APIs can create an added layer of protection between data and a server. To strengthen the security developers tend to add more security measures like tokens, signatures, and transport layer security encryption by implementing API gateways to manage and authenticate traffic and practicing effective API management.

*   **Simplifies**

APIs simplify complex logic by tackling different business logic in chunks. Also provides user-friendly endpoints use cases. It speeds up the development by providing the data developers needed without extra research or manipulation.

### Common API Examples

**Universal Login**

As I mentioned at the start the applications which enable users to log in using Google, Facebook, and Twitter profiles login details. The main aim of using these is to quickly authenticate the user. Which helps to save to set up a profile for each application.

**Third-Party Payment**

This example can be seen in e-commerce applications and also other payment-related apps that help in quick payment using GooglePay, Paytm, and PayPal. Using third-party APIs allows users to complete payment transactions without exposing sensitive data and also helps to avoid granting access to unauthorized persons thus can avoid up to a level of security threat issues.

**Google Maps**

Some food delivery apps and other location-based apps use Google Map services In addition to core maps the apps also can utilize features like geolocation and multiple data layers to communicate with Map API to plot routes or for tracking services.

### API Protocols

To complete the user requirement, API operations will follow protocols(Just like rules, and constraints) to exchange data.

***Remote Procedure Call (RPC)***

Also known as **subroutine/function call**. Web APIs exchange resources based on RPC. This protocol specifies the interaction between client-server(one client request data from the server and the server respond to the client) based applications. **SOAP** is used to implement RPC.

**Service Object Access Protocol(SOAP)**

SOAP is a lightweight protocol for exchanging structured information in a decentralized, distributed environment. It contains the rules especially guiding the request and responses sent from web applications using XML between systems through Hypertext Transfer Protocol(HTTP) or Simple Mail Transfer Protocol(SMTP) for transferring mail.

XML(Extensible Markup Language) is a simple and flexible text format used for data storage and exchange over the internet or other networks. XML defines a set of rules for encoding documents in a format that humans and machines can read.

SOAP APIs are used with enterprise web-based software to ensure high security of transmitted data. One example of SOAP API is PayPal's public API.

**Representational State Transfer(REST)**

It is an alternative to SOAP. It requires writing a lot of code completely for every task and following XML structure for every message sent. REST follows another logic since it makes data available as resources. Each resource is represented as a URL and can request a resource by providing its URL.

These APIs use HTTP requests to work with resources: GET, PUT, HEAD, POST, PATCH, CONNECT, TRACE, OPTIONS and DELETE.

RESTful supportive formats are text, HTML, YAML, XML, and JSON. As it supports multiple formats REST is considered the most popular opinion to develop public APIs. Example: Travel and booking APIs.

**GraphQL**

GraphQL is a Query language for APIs. It provides a simplified description of the data in APIs. Which helps you to get the exact data you need. This makes it easier to evolve APIs over time and also enables powerful developer tools.

### API Documentation

API Documentation is one of the important things to consider after developing and testing the APIs. For a developer to have well-written API documentation is said to be icing on the cake. If you start to work on a project and you get an API to integrate with if the API lacks the documentation the result is that the developer didn’t get how to use the API then the API becomes a piece of trash. There is no use of it then.

Well-written API documentation explains how to effectively use and integrate an API. It includes all the information about the API like classes, returns types, arguments, and functions.

A good API Documentation should have :

*   Start guide
*   Authentication Information
*   API call explanations.
*   Examples of every request and return with a response description, error messages, etc.
*   Tutorials
*   Sample codes
*   SDK examples illustrate how to access the resource likewise.

So there are many API documentation tools to help you. Some of them include:

*   [Postman](https://www.postman.com/api-documentation-tool)
*   [apiDoc](https://apidocjs.com/)
*   [Swagger](https://swagger.io/solutions/api-documentation/)
*   [Reduced](https://redoc.ly/)

Hope you get a little glimpse of APIs. It is relevant in the development field for a programmer. Whatever may be your expertise area whether front-end developer, Android dev, or IOS dev, you should get familiarised with it.

What's your thought about it?

👋👋👋👋👋👋