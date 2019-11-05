#####get()
- Is used inside constructors to resolve the needed instances.
- Instances that are provided using get() must also be defined in a module.
- I advise using named parameters to achieve a better definition & improve readability.

#####factory
- Is used to indicate that a new instance must be created each time it is injected.

This can be done in a couple of ways:

```
class SomeClass(val date: Date) {

    fun getSimpleDate(): String {
        return SimpleDateFormat.getDateInstance().format(date)
    }
}
```
Then
```
val testModule = module {
    // create one instance to be used
    single { Date() }
    // then you can automatically resolve SomeClass
    factory<SomeClass>()
}
```
OR you can use a factory block to compose the service:
```
val testModule = module {
	factory {
        val currentDate = Date()
        return@factory SomeClass(currentDate)
    }
}
```
OR you can resolve an implementation for an with a block:

```
val testModule = module {
	factory<SomeClass> {
       val currentDate = Date()
       return@factory SomeClass(currentDate)
    }
}
```
OR you can resolve an implementation for an interface:

```
val testModule = module {
	factoryBy<SomeInterface, SomeClass>()
}
```

#####single
- Indicates that a unique instance will be created at the beginning and shared on every future injection.

#####name =
is used to name definitions. This is required when you want to have multiple instances of the same class with different types. You can see the Cache class here.

#####viewModel
- Your class must extend the Android ViewModel class.
- Use its constructor for dependency injection:
```
val viewModelModules: Module = module {
         viewModel { SplashScreenViewModel(get()) }
         viewModel { HomeViewModel() }
}
```
- Nothing particular to add to your ViewModel class. Koin will inject the needed dependencies via its constructor

#####Module

- The module definition is very similar to **Dagger-2 @Module** definitions, it serves as a container for a collection of services that should be provided at runtime.

- A module is a central place where you can tell the framework how to create new instances of a dependency.

#####Notes:
- Koin allows late init module definition load so libraries/features can use this quite easily.
- All of the modules (where you define the components) are injected lazily by default, This means that if you never get to open X screen it will never actually inject X ViewModel/Presenter.
- Just call the method loadKoinModules on your library and call that method inside your app’s onCreate.
- Use ``androidContext()`` to provide context.


#####References:

1. https://insert-koin.io/docs/2.0/documentation/reference/index.html#_injection_parameters

2. https://insert-koin.io/docs/2.0/documentation/koin-android/index.html

3. https://android.jlelse.eu/unlock-your-android-viewmodel-power-with-koin-23eda8f493be