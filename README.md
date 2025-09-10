**[View document in Syncfusion Xamarin Knowledge base](https://www.syncfusion.com/kb/12492/how-to-use-drag-indicator-view-with-datatemplateselector-in-xamarin-forms-listview)**

## Sample

```xaml
<ContentPage.Resources>
    <ResourceDictionary>
        <local:MyDataTemplateSelector x:Key="MessageTemplateSelector">
            <local:MyDataTemplateSelector.IncomingDataTemplate>
                <DataTemplate>
                    <code>
                    . . .
                    . . .
                    <code>
                </DataTemplate>
            </local:MyDataTemplateSelector.IncomingDataTemplate>

            <local:MyDataTemplateSelector.OutgoingDataTemplate>
                <DataTemplate>
                    <code>
                    . . .
                    . . .
                    <code>
                </DataTemplate>
            </local:MyDataTemplateSelector.OutgoingDataTemplate>
        </local:MyDataTemplateSelector>
    </ResourceDictionary>
</ContentPage.Resources>

<Grid>
    <sync:SfListView x:Name="listView" 
                ItemTemplate="{StaticResource MessageTemplateSelector}" 
                ItemsSource="{Binding Messages}"
                ItemSize="105"
                SelectionMode="None"
                BackgroundColor="#FFFAF0"
                DragStartMode="OnDragIndicator"/>
</Grid>

DataTemplateSelector:

class MyDataTemplateSelector : Xamarin.Forms.DataTemplateSelector
{
    public DataTemplate IncomingDataTemplate { get; set; }
    public DataTemplate OutgoingDataTemplate { get; set; }

    public MyDataTemplateSelector()
    {
        
    }

    protected override DataTemplate OnSelectTemplate(object item, BindableObject container)
    {
        var messageVm = item as Message;
        if (messageVm == null)
            return null;
        return messageVm.IsIncoming ? this.IncomingDataTemplate : this.OutgoingDataTemplate;
    }
}
```