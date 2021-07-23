# Display API development prerequisites

## Visual Studio

- Visual Studio 2019 (or later)
    - Ensure the .NET desktop development workload is installed (provides support for .NET 4.8, C# and WPF)

## Display API NuGet package

- Access to Atlas.DisplayAPI NuGet package, see [https://github.com/mat-docs/packages](https://github.com/mat-docs/packages)

## ATLAS

- A recent version ATLAS 10 should be installed for testing custom displays

## Required Knowledge

- C#
    - ATLAS has been implemented in the [C# programming language](https://docs.microsoft.com/en-us/dotnet/csharp/tour-of-csharp/) and therefore C# is the preferred implementation language for custom displays
- WPF
    - [Windows Presentation Foundation](https://docs.microsoft.com/en-us/visualstudio/designers/getting-started-with-wpf) is the User Interface technology used by ATLAS and therefore custom displays should also implemented in WPF
- MVVM
    -  [Model-View-ViewModel](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93viewmodel) is a popular software architecture pattern commonly used with WPF applications and therefore ATLAS has been implemented using MVVM and so the Display API has been designed to be fully MVVM compliant, for [Further information](../overview/mvvm.md)

