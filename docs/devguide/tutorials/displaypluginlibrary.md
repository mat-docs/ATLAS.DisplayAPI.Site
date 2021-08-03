# Display Plugin Library

The display plugin library provides base classes and utility classes that reduce the overall effort needed to create a custom display

!!! note

    The code for this library can be reviewed at [Tutorials/DisplayPluginLibrary](https://github.com/mat-docs/Atlas.DisplayAPI.Examples/tree/master/DisplayPluginLibrary)

## `TemplateDisplayViewModelBase` _View Model_ base class

`TemplateDisplayViewModelBase` (substitute for `DisplayPluginViewModel`) provides a template to help follow the [Data request guidelines](..\detailed\data.md#data-request-guidelines)

- Data requests are throttled to 5Hz by default 
    - Pass a different throttle interval to the constructor if the default is not suitable
- Properties are provided for the following common services
    - `IDataRequestSignalFactory DataRequestSignalFactory`
    - `IDisplayParameterService DisplayParameterService`
    - `ILogger Logger`
    - `ISignalBus SignalBus`
- Append additional disposables to the `Disposables` property for automatic cleanup
- Override `OnMakeTimelineDataRequestsAsync` to issue data requests in response to changes to the timebase
- Override `OnMakeCursorDataRequestsAsync` to issue data requests in response to changes to the cursor
- Call `MakeDataRequests` to initiate data requests for any other reason
- Call the `ExecuteOnUiAsync` method to execute code on the UI thread

## `ParameterSampleDisplayViewModelBase` _View Model_ base class

`ParameterSampleDisplayViewModelBase<TParameterViewModel>` (substitute for `TemplateDisplayViewModelBase`) provides automatic retrieval of display parameter(s) sample value at cursor  when the cursor timestamp changes

- `TParameterViewModel` must be a class derived from `ParameterSampleViewModelBase`
- An implementation of the `OnCreateParameterViewModel` factory method must be provided to supply a `TParameterViewModel` instance for a parameter on demand
- `ParameterSampleViewModelBase` base class provides parameter `Name` and `Value` properties and `OnValueChanged` notification method override

## Tracking Operations

The `OperationTracker<TOperation>` class provides support for flow control and throttling of operations such as data requests and redraw.

## Drawing Graphics

WPF provides a number of ways to draw [graphics](https://docs.microsoft.com/en-us/dotnet/desktop/wpf/graphics-multimedia).

The `VisualLayer` class provides a simple way to add graphics drawn using the low-level and efficient [DrawingContext](https://docs.microsoft.com/en-us/dotnet/api/system.windows.media.drawingcontext) class.

!!! attention

    Drawing must be done on the UI thread.

    Make use of [`SynchronizationContext` class](https://docs.microsoft.com/en-us/dotnet/api/system.threading.synchronizationcontext) or `TemplateDisplayViewModelBase.ExecuteOnUiAsync` method.

!!! tip

    To clear the visual layer of all graphics 
    ```c#
    this.TraceVisual.Draw(delegate { });
    ```

## Converters

`ColorToSolidColorBrushValueConverter` is a basic WPF converter that converts a simple colour into a solid colour brush.
