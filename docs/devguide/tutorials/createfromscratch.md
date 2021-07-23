## Create Project

Create a new _C# WPF User Control Library (.NET Framework)_ project within Visual Studio.

!!! tip

    Enter _wpf user_ into the Search box

![Create Project](/assets/images/devguide/tutorials/createproject.png)

!!! caution

    Remember a _.NET Framework WPF_ project and not _.Net Core WPF_ project


![Name Project](/assets/images/devguide/tutorials/nameproject.png)

!!! attention

    Ensure there is _Plugin_ somewhere within the name, otherwise ATLAS will not load the plugin

!!! note

    This project type includes a template for the _View_

## Update Assembly Information

Edit project settings:

![Project Settings](/assets/images/devguide/tutorials/editprojectsettings.png)

Click _Assembly Information..._

![Project Settings](/assets/images/devguide/tutorials/projectsettings.png)

Modify: Title, Description and GUID (if not already set) properties:

![Project Settings](/assets/images/devguide/tutorials/assemblyinformation.png)

_Title_ property corresponds to Display Window title:

![Window Title](/assets/images/devguide/tutorials/windowtitle.png)

_Description_ property corresponds to Display Icon tooltip:

![Icon Tooltip](/assets/images/devguide/tutorials/icontooltip.png)

!!! attention

    A GUID must be specified otherwise ATLAS will fail to start.

    Use Tools->Create GUID as necessary:

    ![Tools Create Guid](/assets/images/devguide/tutorials/toolscreateguid.png)

    Copy Registry Format:

    ![Tools Create Guid](/assets/images/devguide/tutorials/createguid.png)

    Remember to remove '{' and '}' 

## Add reference to Atlas.DisplayAPI NuGet package

Manage NuGet packages of project:

![Manage NuGet Packages](/assets/images/devguide/tutorials/managenugetpackages.png)

Browse to Atlas.DisplayAPI NuGet package and install:

![Manage Package](/assets/images/devguide/tutorials/nugetpackage.png)

Once installed the references will be:

![Manage Package](/assets/images/devguide/tutorials/references.png)

## Add an icon for the toolbar

Add _Resources_ folder to project:

![Add Resources Folder](/assets/images/devguide/tutorials/addresourcesfolder.png)

Which should look like:

![Resources Folder](/assets/images/devguide/tutorials/resourcesfolder.png)

Add existing item to Resources folder:

![Resources Folder](/assets/images/devguide/tutorials/addiconasexistingitem.png)

Select and _Add_ icon:

![Resources Folder](/assets/images/devguide/tutorials/selectandaddicon.png)

Which should look like:

![Resources Folder](/assets/images/devguide/tutorials/icon.png)

Ensure _Build Action_ is set to _Resource_:

![Resources Folder](/assets/images/devguide/tutorials/iconproperties.png)

## Rename and update View

- Rename `UserControl1` to `SampleDisplayView`
    - Rename `UserControl1.xaml` to `SampleDIsplayView.xaml`
        - Update `x:Class` to `SampleDisplayPlugin.SampleDisplayView`
    - Rename `UserControl1.xaml.cs` to `SampleDIsplayView.xaml.cs`
        - Rename `UserControl1` class to `SampleDisplayView`

    ```c#
    namespace SampleDisplayPlugin
    {
        public partial class SampleDisplayView
        {
            public SampleDisplayView()
            {
                InitializeComponent();
            }
        }
    }
    ```

- Add a simple `<TextBlock>` to display white text to the _XAML_

    ```xml hl_lines="9-13"
    <UserControl x:Class="SampleDisplayPlugin.SampleDisplayView"
                 xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
                 xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
                 xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
                 xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
                 mc:Ignorable="d"
                 d:DesignHeight="450" d:DesignWidth="800">
        <Grid>
            <TextBlock VerticalAlignment="Center"
                       HorizontalAlignment="Center"
                       Foreground="White"
                       FontSize="20"
                       Text="My First Display" />
        </Grid>
    </UserControl>
    ```

!!! note

    White text since window background is black by default
