# How to set the default display text for GridComboBox column in WPF DataGrid (SfDataGrid)?

This sample show cases how to set the default display text for GridComboBox column in [WPF DataGrid](https://www.syncfusion.com/wpf-ui-controls/datagrid) (SfDataGrid)?

# About the sample
The [GridComboBoxColumn](https://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.Grid.GridComboBoxColumn.html) does not have direct support to display default text on it when there is no selected Item in [WPF DataGrid](https://www.syncfusion.com/wpf-ui-controls/datagrid) (SfDataGrid). You can change the default text using ComboBoxValueConverter and DisplayBinding property of the column.

```Xaml
<Window.Resources>
    <local:ComboBoxValueConverter x:Key="comboBoxValueConverter"/>
</Window.Resources>
<syncfusion:SfDataGrid Name="dataGrid"
                        AutoGenerateColumns="False"
                        AllowEditing="True"
                        ColumnSizer="Auto"
                        ItemsSource="{Binding Employees}">
    <syncfusion:SfDataGrid.Columns>
        <syncfusion:GridTextColumn MappingName="FirstName" HeaderText="First Name" ColumnFilter="DisplayText" />
        <syncfusion:GridTextColumn  MappingName="LastName" HeaderText="Last Name" />
        <syncfusion:GridTextColumn MappingName="ID"/>
        <syncfusion:GridTextColumn  MappingName="Title" />
        <syncfusion:GridTextColumn  MappingName="Salary" />
        <syncfusion:GridComboBoxColumn MappingName="ReportsTo" HeaderText="Reports To" ItemsSource="{Binding Reporters}" DisplayBinding="{Binding Path=ReportsTo, Converter={StaticResource comboBoxValueConverter}}"/>
    </syncfusion:SfDataGrid.Columns>
</syncfusion:SfDataGrid>
```
```c#
public class ComboBoxValueConverter : IValueConverter
{
    public object Convert(object value, Type targetType, object parameter, CultureInfo culture)
    {
        if (string.IsNullOrEmpty(value.ToString()))
            value = "Select a Value";
        return value;
    }

    public object ConvertBack(object value, Type targetType, object parameter, CultureInfo culture)
    {
        throw new NotImplementedException();
    }
}
```

KB article - [How to set the default display text for GridComboBox column in WPF DataGrid (SfDataGrid)?](https://www.syncfusion.com/kb/11999/how-to-set-the-default-display-text-for-gridcombobox-column-in-wpf-datagrid-sfdatagrid)

## Requirements to run the demo
 Visual Studio 2015 and above versions
