MVVM is a popular software architecture pattern commonly used with WPF applications:

![MVVM](/assets/images/overview/mvvm.png)

- _Model-View-ViewModel_ pattern
    - _2 way binding_
        - `DataContext` _View_ property should be assigned an implementation of the _View Model_
        - `“{Binding …}”` _XAML_ element link a _View_ property to _View Model_ property
    - _Change notification_
        - _View Model_ should implement the `INotifyPropertyChanged` interface
            - `PropertyChanged` event should be raised when property value changes
    - _Commands_
        - _View Model_ must provide an implementation of the `ICommand` interface per _command_ 
- Helper classes
    - `BindableBase` base class
        - Implements `INotifyPropertyChanged`
        - Provides `SetProperty` methods to simplify following the pattern
    - `DisposableBindableBase` base class
        - As per `BindableBase` but also supports `IDisposable`
    - `DelegateCommand` class
        - Provides a generic implementation of `ICommand` for _commands_