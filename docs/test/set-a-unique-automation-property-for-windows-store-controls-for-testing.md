---
title: Ustawianie unikatowej właściwości automatyzacji dla kontrolek platformy UWP przeznaczonych do testowania
ms.date: 05/31/2018
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
author: mikejo5000
ms.openlocfilehash: 51e16dcaa48a08ae97bc80be1d33163c6f3af875
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590452"
---
# <a name="set-a-unique-automation-property-for-uwp-controls-for-testing"></a>Ustawianie unikatowej właściwości automatyzacji dla kontrolek platformy UWP do testowania

Jeśli chcesz uruchomić kodowane testy interfejsu użytkownika dla aplikacji platformy UWP opartej na języku XAML, każdy formant musi być identyfikowany przez unikatową Właściwość automatyzacji. Można przypisać unikatową Właściwość automatyzacji w oparciu o typ kontrolki XAML w aplikacji.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="static-xaml-definition"></a>Statyczna definicja XAML

Aby określić unikatową Właściwość automatyzacji dla kontrolki, która jest zdefiniowana w pliku XAML, można ustawić **AutomationProperties. AutomationId** lub **AutomationProperties.Name** niejawnie lub jawnie, jak pokazano w poniższym przykładzie. Ustawienie jednej z tych wartości daje formantowi unikatową Właściwość automatyzacji, która może służyć do identyfikowania kontrolki podczas tworzenia kodowanego testu interfejsu użytkownika lub rejestrowania akcji.

### <a name="set-the-property-implicitly"></a>Ustaw właściwość jako niejawnie

Ustaw **AutomationProperties. AutomationId** na **ButtonX** przy użyciu właściwości **name** w kodzie XAML dla kontrolki.

```xaml
<Button Name="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />
```

Ustaw **AutomationProperties.Name** na **przycisk** przy użyciu właściwości **Content** w kodzie XAML dla kontrolki.

```xaml
<Button Content="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />
```

### <a name="set-the-property-explicitly"></a>Ustaw właściwość jawnie

Ustaw **AutomationProperties. AutomationId** na **ButtonX** jawnie w kodzie XAML dla kontrolki.

```xaml
<Button AutomationProperties.AutomationId="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />
```

Ustaw **AutomationProperties.Name** na **przycisk** jawnie w kodzie XAML dla kontrolki.

```xaml
<Button AutomationProperties.Name="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />
```

## <a name="assign-unique-names"></a>Przypisywanie unikatowych nazw

W Blend for Visual Studio można wybrać opcję przypisywania unikatowych nazw do elementów interaktywnych, takich jak przyciski, pola listy, pola kombi i pola tekstowe, które dają kontrolki unikatowe wartości dla **AutomationProperties.Name**.

Aby przypisać unikatowe nazwy do istniejących kontrolek, wybierz pozycję **narzędzia** > **Nazwij elementy interaktywne**.

![Nazwij elementy interaktywne w Blend for Visual Studio](../test/media/cuit_windowsstoreproperty_blend_1.png)

Aby automatycznie nadać unikatową nazwę nowym kontrolkom, wybierz pozycję **narzędzia** > **Opcje** , aby otworzyć okno dialogowe **Opcje** . Wybierz pozycję **Projektant XAML** a następnie wybierz pozycję **automatycznie Nazwij elementy interaktywne podczas tworzenia**. Wybierz przycisk **OK**, aby zamknąć okno dialogowe.

## <a name="use-a-data-template"></a>Korzystanie z szablonu danych

Można zdefiniować prosty szablon przy użyciu **ItemTemplate** , aby powiązać wartości w polu listy z zmiennymi:

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

Można również użyć szablonu z **ItemContainerStyle** , aby powiązać wartości ze zmiennymi:

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

W obu tych przykładach należy zastąpić metodę **ToString ()** **ustawieniem właściwości ItemSource**, jak pokazano w poniższym przykładzie kodu. Ten kod sprawdza, czy wartość **AutomationProperties.Name** jest ustawiona i jest unikatowa, ponieważ nie można ustawić unikatowej właściwości automatyzacji dla każdego elementu listy powiązanego z danymi przy użyciu powiązania. W takim przypadku ustawienie unikatowej wartości **Properties.Name automatyzacji** jest wystarczające.

> [!NOTE]
> Korzystając z tego podejścia, wewnętrzna zawartość elementu listy może być również ustawiona na ciąg w klasie Employee za pośrednictwem powiązania. Jak pokazano w przykładzie, kontrolka przycisku wewnątrz każdego elementu listy ma przypisany unikatowy identyfikator automatyzacji, który jest IDENTYFIKATORem pracownika.

```csharp
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

## <a name="use-a-control-template"></a>Używanie szablonu kontrolki

Można użyć szablonu kontrolki, aby każde wystąpienie określonego typu uzyskało unikatową Właściwość automatyzacji, gdy jest zdefiniowana w kodzie. Utwórz szablon, tak aby **AutomationProperty** powiązać z UNIKATOWYm identyfikatorem w wystąpieniu formantu. Poniższy kod XAML ilustruje jedno z podejścia do utworzenia tego powiązania z szablonem formantu:

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

Podczas definiowania dwóch wystąpień przycisku przy użyciu tego szablonu kontrolki identyfikator automatyzacji jest ustawiany na unikatowy ciąg zawartości dla kontrolek w szablonie, jak pokazano w poniższym kodzie XAML:

```xaml
<Button Content="Button1" Style="{StaticResource MyButton}" Width="140"/>
<Button Content="Button2" Style="{StaticResource MyButton}" Width="140"/>
```

### <a name="dynamic-controls"></a>Formanty dynamiczne

Jeśli masz formanty, które są tworzone dynamicznie z kodu i nie są tworzone statycznie lub za pomocą szablonów w plikach XAML, musisz ustawić właściwości **zawartości** lub **nazwy** dla kontrolki. Ta akcja gwarantuje, że każda kontrolka dynamiczna ma unikatową Właściwość automatyzacji. Na przykład jeśli masz pole wyboru, które musi być wyświetlane po wybraniu elementu listy, możesz ustawić te właściwości, jak pokazano poniżej:

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

## <a name="see-also"></a>Zobacz także

- [Testowanie aplikacji platformy UWP przy użyciu kodowanych testów interfejsu użytkownika](../test/test-uwp-app-with-coded-ui-test.md)
