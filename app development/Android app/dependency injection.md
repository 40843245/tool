# library about dependency injection
## Dagger
[Dagger](https://dagger.dev/) is a popular dependency injection library for Java, Kotlin, and Android that is maintained by Google. Dagger facilitates using DI in your app by creating and managing the graph of dependencies for you. 

It provides fully static and compile-time dependencies addressing many of the development and performance issues of reflection-based solutions such as [Guice](https://en.wikipedia.org/wiki/Google_Guice).

## Hilt
Hilt is Jetpack's recommended library for dependency injection in Android. Hilt defines a standard way to do DI in your application by providing containers for every Android class in your project and managing their lifecycles automatically for you.

Hilt is built on top of the popular DI library Dagger to benefit from the compile time correctness, runtime performance, scalability, and Android Studio support that Dagger provides.

To learn more about Hilt, see [Dependency Injection with Hilt(Android Studio official docs)](https://developer.android.com/training/dependency-injection/hilt-android).
