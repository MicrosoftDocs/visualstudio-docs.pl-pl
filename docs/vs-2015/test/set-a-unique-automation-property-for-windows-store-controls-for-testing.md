---
title: Ustawianie unikatowej właściwości automatyzacji dla kontrolek sklepu Windows na potrzeby testowania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 9bdd74ff-2534-4fc7-a5c3-a77bf7843037
caps.latest.revision: 12
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d4ccf10f3ce085aa8f0275c40644f1a109616daf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672138"
---
# <a name="set-a-unique-automation-property-for-windows-store-controls-for-testing"></a>Ustawianie unikatowej właściwości automatyzacji dla kontrolek Sklepu Windows przeznaczonych do testowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli chcesz uruchomić kodowane testy interfejsu użytkownika dla aplikacji ze sklepu Windows opartej na języku XAML, musisz mieć unikatową Właściwość automatyzacji, która identyfikuje każdy formant.

 Można przypisać unikatową Właściwość automatyzacji w oparciu o typ kontrolki XAML w aplikacji. Poniżej przedstawiono sposób przypisywania tej unikatowej właściwości automatyzacji w następujących sytuacjach:

- [Statyczna definicja XAML formantów](#UniquePropertyWindowsStoreControlsStaticXAML)

- [Przypisywanie unikatowych właściwości automatyzacji przy użyciu programu Visual Studio lub Blend for Visual Studio](#UniquePropertyWindowsStoreControlsExpressionBlend)

- [Korzystanie z szablonu DataTemplate](#UniquePropertyWindowsStoreControlsDataTemplate)

- [Używanie szablonu kontrolki](#UniquePropertyWindowsStoreControlsControlTemplate)

- [Formanty dynamiczne](#UniquePropertyWindowsStoreControlsDynamicControls)

## <a name="use-methods-to-assign-a-unique-automation-property"></a>Używanie metod do przypisywania unikatowej właściwości automatyzacji

### <a name="static-xaml-definition"></a><a name="UniquePropertyWindowsStoreControlsStaticXAML"></a> Statyczna definicja XAML
 Aby określić unikatową Właściwość automatyzacji dla kontrolki, która jest zdefiniowana w pliku XAML, można ustawić AutomationProperties. AutomationId lub AutomationProperties.Name niejawnie lub jawnie, jak pokazano w poniższych przykładach. Ustawienie jednej z tych wartości daje formantowi unikatową Właściwość automatyzacji, która może służyć do identyfikowania kontrolki podczas tworzenia kodowanego testu interfejsu użytkownika lub rejestrowania akcji.

 **Ustaw właściwość jako niejawnie**

 Ustaw właściwość AutomationProperties. AutomationId na **ButtonX** przy użyciu właściwości Name w kodzie XAML dla kontrolki.

```xaml
<Button Name="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />

```

 Ustaw AutomationProperties.Name na **przycisk** za pomocą właściwości content w kodzie XAML dla kontrolki.

```xaml
<Button Content="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />

```

 **Ustaw właściwość jawnie**

 Ustaw AutomationProperties. AutomationId na **ButtonX** jawnie w kodzie XAML dla kontrolki.

```xaml
<Button AutomationProperties.AutomationId=“ButtonX” Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />

```

 Ustaw AutomationProperties.Name na **przycisk** jawnie w kodzie XAML dla kontrolki.

```
<Button AutomationProperties.Name="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />
```

### <a name="assign-unique-automation-properties-using-visual-studio-or-blend-for-visual-studio"></a><a name="UniquePropertyWindowsStoreControlsExpressionBlend"></a> Przypisywanie unikatowych właściwości automatyzacji przy użyciu programu Visual Studio lub Blend for Visual Studio
 Możesz użyć programu Visual Studio lub Blend for Visual Studio do przypisywania unikatowych nazw do elementów interaktywnych, takich jak przyciski, pola listy, pola kombi i pola tekstowe. Daje to kontrolce unikatową wartość dla AutomationProperties.Name.

 **Program Visual Studio:** W menu **Narzędzia** wskaż polecenie **Opcje** , a następnie wybierz **Edytor tekstu**, **XAML**i **inne**.

 Wybierz pozycję **automatycznie Nazwij elementy interaktywne podczas tworzenia** , a następnie wybierz przycisk **OK**.

 ![Opcje różne XAML](../test/media/cuit-windowsstoreapp-b.png "CUIT_WindowsStoreApp_B")

 **Blend for Visual Studio:** Użyj jednej z następujących metod, aby wykonać tę czynność z Blend for Visual Studio.

> [!NOTE]
> Tej metody można używać tylko w przypadku formantów, które są tworzone statycznie przy użyciu języka XAML.

 **Aby przypisać unikatową nazwę do istniejących kontrolek**

 W menu **Narzędzia** wybierz pozycję **Nazwij elementy interaktywne**, jak pokazano poniżej:

 ![Wybierz pozycję Nazwij elementy interaktywne z menu Narzędzia](../test/media/cuit-windowsstoreproperty-blend-1.png "CUIT_WindowsStoreProperty_Blend_1")

 **Aby automatycznie nadać unikatową nazwę kontrolkom, które tworzysz**

 W menu **Narzędzia** wskaż polecenie **Opcje**, a następnie wybierz **projekt**. Wybierz pozycję **automatycznie Nazwij elementy interaktywne podczas tworzenia** , a następnie wybierz przycisk **OK**, jak pokazano poniżej:

 ![Ustaw nazwę projektu na elementy interaktywne](../test/media/cuit-windowsstoreproeprty-blend-2.png "CUIT_WindowsStoreProeprty_Blend_2")

### <a name="use-a-data-template"></a><a name="UniquePropertyWindowsStoreControlsDataTemplate"></a> Korzystanie z szablonu danych
 Można zdefiniować prosty szablon przy użyciu ItemTemplate, aby powiązać wartości w polu listy z zmiennymi przy użyciu następującego kodu XAML.

```xaml

<ListBox Name="listBox1" ItemsSource="{Binding Source={StaticResource employees}}">
   <ListBox.ItemTemplate>
      <DataTemplate>
         <StackPanel Orientation="Horizontal">
            <TextBlock Text="{Binding EmployeeName}" />
            <TextBlock Text="{Binding EmployeeID}" />
         </StackPanel>
      </DataTemplate>
   </ListBox.ItemTemplate>
</ListBox>
```

 Można również użyć szablonu z ItemContainerStyle, aby powiązać wartości ze zmiennymi przy użyciu następującego kodu XAML.

```xaml

      <ListBox Name="listBox1" ItemsSource="{Binding Source={StaticResource employees}}">
            <ListBox.ItemContainerStyle>
                <Style TargetType="ListBoxItem">
                    <Setter Property="Template">
                        <Setter.Value>
                            <ControlTemplate TargetType="ListBoxItem">
                                <Grid>
                                    <Button Content="{Binding EmployeeName}" AutomationProperties.AutomationId="{Binding EmployeeID}"/>
                                </Grid>
                            </ControlTemplate>
                        </Setter.Value>
                    </Setter>
                </Style>
            </ListBox.ItemContainerStyle>        
        </ListBox>

```

 W obu tych przykładach należy zastąpić metodę ToString () ustawieniem właściwości ItemSource, jak pokazano w poniższym kodzie. Ten kod sprawdza, czy wartość AutomationProperties.Name jest ustawiona i jest unikatowa, ponieważ nie można ustawić unikatowej właściwości automatyzacji dla każdego elementu listy powiązanego z danymi przy użyciu powiązania. W takim przypadku ustawienie unikatowej wartości Properties.Name automatyzacji jest wystarczające.

> [!NOTE]
> Korzystając z tego podejścia, wewnętrzna zawartość elementu listy może być również ustawiona na ciąg w klasie Employee za pośrednictwem powiązania. Jak pokazano w przykładzie, kontrolka przycisku wewnątrz każdego elementu listy ma przypisany unikatowy identyfikator automatyzacji, który jest IDENTYFIKATORem pracownika.

```

Employee[] employees = new Employee[]
{
   new Employee("john", "4384"),
   new Employee("margaret", "7556"),
   new Employee("richard", "8688"),
   new Employee("george", "1293")
};

listBox1.ItemsSource = employees;

public override string ToString()
{
    return EmployeeName + EmployeeID; // Unique Identification to be set as the AutomationProperties.Name
}

```

### <a name="use-a-control-template"></a><a name="UniquePropertyWindowsStoreControlsControlTemplate"></a> Używanie szablonu kontrolki
 Można użyć szablonu kontrolki, aby każde wystąpienie określonego typu uzyskało unikatową Właściwość automatyzacji, gdy jest zdefiniowana w kodzie. Należy utworzyć szablon, tak aby AutomationProperty powiązać z unikatowym IDENTYFIKATORem w wystąpieniu formantu. Poniższy kod XAML ilustruje jedno z podejście do utworzenia tego powiązania z szablonem kontrolki.

```xaml

<Style x:Key="MyButton" TargetType="Button">
<Setter Property="Template">
   <Setter.Value>
<ControlTemplate TargetType="Button">
   <Grid>
      <CheckBox HorizontalAlignment="Left" AutomationProperties.AutomationId="{TemplateBinding Content}"></CheckBox>
      <Button Width="90" HorizontalAlignment="Right" Content="{TemplateBinding Content}" AutomationProperties.AutomationId="{TemplateBinding Content}"></Button>
   </Grid>
</ControlTemplate>
   </Setter.Value>
</Setter>
</Style>

```

 Podczas definiowania dwóch wystąpień przycisku przy użyciu tego szablonu kontrolki identyfikator automatyzacji jest ustawiany na unikatowy ciąg zawartości dla kontrolek w szablonie, jak pokazano w poniższym kodzie XAML.

```xaml

<Button Content=”Button1” Style="{StaticResource MyButton}" Width="140"/>
<Button Content=”Button2” Style="{StaticResource MyButton}" Width="140"/>
```

### <a name="dynamic-controls"></a><a name="UniquePropertyWindowsStoreControlsDynamicControls"></a> Formanty dynamiczne
 Jeśli masz formanty, które są tworzone dynamicznie z kodu i nie są tworzone statycznie lub za pomocą szablonów w plikach XAML, musisz ustawić właściwości zawartości lub nazwy dla kontrolki. Daje to pewność, że każda dynamiczna kontrola ma unikatową Właściwość automatyzacji. Na przykład jeśli masz pole wyboru, które musi być wyświetlane po wybraniu elementu listy, możesz ustawić te właściwości, jak pokazano poniżej:

```csharp

private void CreateCheckBox(string txt, StackPanel panel)
   {
      CheckBox cb = new CheckBox();
      cb.Content = txt; // Sets the AutomationProperties.Name
      cb.Height = 50;
      cb.Width = 100;
      cb.Name = "DynamicCheckBoxAid"+ txt; // Sets the AutomationProperties.AutomationId
      panel.Children.Add(cb);
    }

```
