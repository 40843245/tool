# library about dependency injection
## Dagger
[Dagger](https://dagger.dev/) is a popular dependency injection library for Java, Kotlin, and Android that is maintained by Google. Dagger facilitates using DI in your app by creating and managing the graph of dependencies for you. 

It provides fully static and compile-time dependencies addressing many of the development and performance issues of reflection-based solutions such as [Guice](https://en.wikipedia.org/wiki/Google_Guice).

### [Dagger module](https://developer.android.com/training/dependency-injection/dagger-android#dagger-modules)
A Dagger module is a class that is annotated with `@Module`.

## Hilt
Hilt is Jetpack's recommended library for dependency injection in Android. Hilt defines a standard way to do DI in your application by providing containers for every Android class in your project and managing their lifecycles automatically for you.

Hilt is built on top of the popular DI library Dagger to benefit from the compile time correctness, runtime performance, scalability, and Android Studio support that Dagger provides.

To learn more about Hilt, see [Dependency Injection with Hilt(Android Studio official docs)](https://developer.android.com/training/dependency-injection/hilt-android).

### [Hilt Module](https://developer.android.com/training/dependency-injection/hilt-android#hilt-modules)
A Hilt module is a class that is annotated with `@Module`.

## Comparison table

| | Dagger module | Hilt module |
| - | ----------- | ----------- |
|   |  it informs Hilt how to provide instances of certain types |  it informs Hilt how to provide instances of certain types |
|   |  it is a class that is annotated with `@Module` | it is a class that is annotated with `@Module` |
|   | one can define dependencies with the `@Provides` annotation | one must annotate with `@InstallIn` to tell Hilt which Android class each module will be used or installed in |


