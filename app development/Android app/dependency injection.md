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

#### inject something with Hilt module
###### [interface instance (with `@Binds`)](https://developer.android.com/training/dependency-injection/hilt-android#inject-interfaces)
Consider the following example.

```
interface AnalyticsService {
  fun analyticsMethods()
}

// Constructor-injected, because Hilt needs to know how to
// provide instances of AnalyticsServiceImpl, too.
class AnalyticsServiceImpl @Inject constructor(
  ...
) : AnalyticsService { ... }

@Module
@InstallIn(ActivityComponent::class)
abstract class AnalyticsModule {

  @Binds
  abstract fun bindAnalyticsService(
    analyticsServiceImpl: AnalyticsServiceImpl
  ): AnalyticsService
}
```

##### [Inject instances with `@Provides`](https://developer.android.com/training/dependency-injection/hilt-android#inject-provides)
Consider the following example.

```
@Module
@InstallIn(ActivityComponent::class)
object AnalyticsModule {

  @Provides
  fun provideAnalyticsService(
    // Potential dependencies of this type
  ): AnalyticsService {
      return Retrofit.Builder()
               .baseUrl("https://example.com")
               .build()
               .create(AnalyticsService::class.java)
  }
}
```

#### [Provide multiple bindings for the same type](https://developer.android.com/training/dependency-injection/hilt-android#multiple-bindings)
Consider the following example.

If you need to intercept calls to `AnalyticsService`, you could use an `OkHttpClient` object with an interceptor. 

For other services, you might need to intercept calls in a different way. 

In that case, you need to tell Hilt how to provide two different implementations of `OkHttpClient`.

1. First, define the qualifiers (i.e. class that with qualifier annotation) that you will use to annotate the `@Binds` or `@Provides` methods.

```
@Qualifier
@Retention(AnnotationRetention.BINARY)
annotation class AuthInterceptorOkHttpClient

@Qualifier
@Retention(AnnotationRetention.BINARY)
annotation class OtherInterceptorOkHttpClient
```

2. Then, Hilt needs to know how to provide an instance of the type that corresponds with each qualifier.

In this case, you could use a Hilt module with `@Provides`. Both methods have the same return type, but the qualifiers label them as two different bindings.

```
@Module
@InstallIn(SingletonComponent::class)
object NetworkModule {

  @AuthInterceptorOkHttpClient
  @Provides
  fun provideAuthInterceptorOkHttpClient(
    authInterceptor: AuthInterceptor
  ): OkHttpClient {
      return OkHttpClient.Builder()
               .addInterceptor(authInterceptor)
               .build()
  }

  @OtherInterceptorOkHttpClient
  @Provides
  fun provideOtherInterceptorOkHttpClient(
    otherInterceptor: OtherInterceptor
  ): OkHttpClient {
      return OkHttpClient.Builder()
               .addInterceptor(otherInterceptor)
               .build()
  }
}
```

3. Next, you can inject the specific type that you need by annotating the field or parameter with the corresponding qualifier.

```
// As a dependency of another class.
@Module
@InstallIn(ActivityComponent::class)
object AnalyticsModule {

  @Provides
  fun provideAnalyticsService(
    @AuthInterceptorOkHttpClient okHttpClient: OkHttpClient
  ): AnalyticsService {
      return Retrofit.Builder()
               .baseUrl("https://example.com")
               .client(okHttpClient)
               .build()
               .create(AnalyticsService::class.java)
  }
}

// As a dependency of a constructor-injected class.
class ExampleServiceImpl @Inject constructor(
  @AuthInterceptorOkHttpClient private val okHttpClient: OkHttpClient
) : ...

// At field injection.
@AndroidEntryPoint
class ExampleActivity: AppCompatActivity() {

  @AuthInterceptorOkHttpClient
  @Inject lateinit var okHttpClient: OkHttpClient
}
```

#### [Predefined qualifiers in Hilt](https://developer.android.com/training/dependency-injection/hilt-android#predefined-qualifiers)
Suppose that the `AnalyticsAdapter` class from the above example needs the context of the activity. The following code demonstrates how to provide the activity context to `AnalyticsAdapter`.

```
class AnalyticsAdapter @Inject constructor(
    @ActivityContext private val context: Context,
    private val service: AnalyticsService
) { ... }
```

For more predefined bindings available in Hilt, see [Component default bindings](https://developer.android.com/training/dependency-injection/hilt-android#component-default)

### [Generated components for Android classes](https://developer.android.com/training/dependency-injection/hilt-android#generated-components)
Hilt provides the following components.

| Hilt component |	Injector for |
| -------------- | ------------- |
| SingletonComponent	| Application |
| ActivityRetainedComponent	| N/A |
| ViewModelComponent	| ViewModel |
| ActivityComponent	| Activity |
| FragmentComponent	| Fragment |
| ViewComponent	| View |
| ViewWithFragmentComponent	| View annotated with @WithFragmentBindings |
| ServiceComponent | Service |

**NOTES**

Hilt doesn't generate a component for broadcast receivers because Hilt injects broadcast receivers directly from `SingletonComponent`.

#### [Component lifetimes](https://developer.android.com/training/dependency-injection/hilt-android#component-lifetimes)

| Generated component	| Created at | Destroyed at |
| ------------------- | ---------- | ------------ |
| SingletonComponent | Application#onCreate()	| Application destroyed |
| ActivityRetainedComponent	| Activity#onCreate()	| Activity#onDestroy() |
| ViewModelComponent	| ViewModel created	| ViewModel destroyed |
| ActivityComponent	| Activity#onCreate()	| Activity#onDestroy() |
| FragmentComponent	| Fragment#onAttach()	| Fragment#onDestroy() |
| ViewComponent	| View#super() | View destroyed |
| ViewWithFragmentComponent	| View#super() | View destroyed |
| ServiceComponent | Service#onCreate()	| Service#onDestroy() |

**NOTES**

`ActivityRetainedComponent` lives across configuration changes, so it is created at the first `Activity#onCreate()` and destroyed at the last `Activity#onDestroy()`.

#### [Component scopes](https://developer.android.com/training/dependency-injection/hilt-android#component-scopes)
| Android class	| Generated component	| Scope |
| ------------- | ------------------- | ----- |
| Application	| SingletonComponent| @Singleton |
| Activity | ActivityRetainedComponent | @ActivityRetainedScoped |
| ViewModel | ViewModelComponent | @ViewModelScoped |
| Activity | ActivityComponent | @ActivityScoped |
| Fragment | FragmentComponent | @FragmentScoped |
| View | ViewComponent | @ViewScoped |
| View annotated with @WithFragment Bindings | ViewWithFragmentComponent| @ViewScoped |
| Service	| ServiceComponent | @ServiceScoped |

To learn more about Hilt component scopes, see [Scoping in Android and Hilt](https://medium.com/androiddevelopers/scoping-in-android-and-hilt-c2e5222317c0).

##### Example

```
@ActivityScoped
class AnalyticsAdapter @Inject constructor(
  private val service: AnalyticsService
) { ... }
```

##### [Scoping in Android](https://medium.com/androiddevelopers/scoping-in-android-and-hilt-c2e5222317c0)

Here an example.

```
class ExampleActivity : AppCompatActivity() {
  private val analyticsAdapter = AnalyticsAdapter()
  ...
}
```

is equivalent to

```
@ActivityScoped
class AnalyticsAdapter @Inject constructor() { ... }
@AndroidEntryPoint
class ExampleActivity : AppCompatActivity() {
  @Inject lateinit var analyticsAdapter: AnalyticsAdapter
}
```

with Hilt.

#### [Component hierarchy](https://developer.android.com/training/dependency-injection/hilt-android#component-hierarchy)

![image](file:///C:/Users/40843/Downloads/hilt-hierarchy.svg)

## Comparison table

| Dagger module | Hilt module |
| ----------- | ----------- |
|  it informs Hilt how to provide instances of certain types |  it informs Hilt how to provide instances of certain types |
|  it is a class that is annotated with `@Module` | it is a class that is annotated with `@Module` |
| one can define dependencies with the `@Provides` annotation | one must annotate with `@InstallIn` to tell Hilt which Android class each module will be used or installed in |


