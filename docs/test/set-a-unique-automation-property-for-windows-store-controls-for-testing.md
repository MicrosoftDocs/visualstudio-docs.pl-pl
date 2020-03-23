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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590452"
---
# <a name="set-a-unique-automation-property-for-uwp-controls-for-testing"></a>Ustawianie unikatowej właściwości automatyzacji dla formantów platformy uniwersalnej systemu uniwersalnego do testowania

Jeśli chcesz uruchomić kodowane testy interfejsu użytkownika dla aplikacji platformy uniwersalnej systemu i kontroli 15 platformy uniwersalnej systemu XAML, każdy formant musi być identyfikowany przez unikatową właściwość automatyzacji. Można przypisać unikatową właściwość automatyzacji na podstawie typu formantu XAML w aplikacji.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="static-xaml-definition"></a>Statyczna definicja XAML

Aby określić unikatową właściwość automatyzacji dla formantu, który jest zdefiniowany w pliku XAML, można ustawić **AutomationProperties.AutomationId** lub **AutomationProperties.Name** niejawnie lub jawnie, jak pokazano w kolejnych przykładach. Ustawienie jednej z tych wartości daje kontroli unikatową właściwość automatyzacji, która może służyć do identyfikowania formantu podczas tworzenia kodowany test interfejsu użytkownika lub rejestrowanie akcji.

### <a name="set-the-property-implicitly"></a>Ustaw właściwość niejawnie

Ustaw **AutomationProperties.AutomationId** do **ButtonX** przy użyciu **Name** właściwości w XAML formantu.

```xaml
<Button Name="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />
```

Ustaw **AutomationProperties.Name** **buttony** przy użyciu **content** właściwości w XAML formantu.

```xaml
<Button Content="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />
```

### <a name="set-the-property-explicitly"></a>Ustaw właściwość jawnie

Ustaw **AutomationProperties.AutomationId** **do ButtonX** jawnie w XAML dla formantu.

```xaml
<Button AutomationProperties.AutomationId="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />
```

Ustaw **AutomationProperties.Name** **ButtonY** jawnie w XAML dla formantu.

```xaml
<Button AutomationProperties.Name="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />
```

## <a name="assign-unique-names"></a>Przypisywanie unikatowych nazw

W programie Blend for Visual Studio można wybrać opcję przypisywania unikatowych nazw do elementów interaktywnych, takich jak przyciski, pola listy, pola kombi i pola tekstowe, co daje formanty unikatowe wartości **dla AutomationProperties.Name**.

Aby przypisać unikatowe nazwy do istniejących formantów, wybierz pozycję **Nazwy narzędzi** > **Elementy interaktywne**.

![Nazwij elementy interaktywne w programie Blend for Visual Studio](../test/media/cuit_windowsstoreproperty_blend_1.png)

Aby automatycznie nadać unikatowe nazwy nowym dodaniu formantów, wybierz pozycję**Opcje** **narzędzi,** > aby otworzyć okno dialogowe **Opcje.** Wybierz **projektanta XAML,** a następnie wybierz pozycję **Automatycznie nazwij elementy interaktywne podczas tworzenia**. Wybierz przycisk **OK**, aby zamknąć okno dialogowe.

## <a name="use-a-data-template"></a>Używanie szablonu danych

Prosty szablon można zdefiniować za pomocą **itemTemplate,** aby powiązać wartości w polu listy ze zmiennymi:

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

Można również użyć szablonu z **ItemContainerStyle** do powiązania wartości ze zmiennymi:

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

W obu tych przykładach należy następnie zastąpić **ToString()** metoda **ItemSource**, jak pokazano przy użyciu przykładu kodu, który poniżej. Ten kod zapewnia, że **AutomationProperties.Name** wartość jest ustawiona i jest unikatowa, ponieważ nie można ustawić unikatową właściwość automatyzacji dla każdego elementu listy powiązanej z danymi przy użyciu powiązania. Ustawienie unikatowej wartości dla **automatyzacji Properties.Name** jest wystarczające w tym przypadku.

> [!NOTE]
> Przy użyciu tego podejścia wewnętrzna zawartość elementu listy można również ustawić na ciąg w Employee klasy za pośrednictwem powiązania. Jak pokazano w przykładzie, formant przycisku wewnątrz każdego elementu listy jest przypisany unikatowy identyfikator automatyzacji, który jest identyfikatorem pracownika.

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

## <a name="use-a-control-template"></a>Używanie szablonu formantu

Można użyć szablonu formantu, tak aby każde wystąpienie określonego typu uzyskuje unikatową właściwość automatyzacji, gdy jest zdefiniowana w kodzie. Utwórz szablon, tak aby **AutomationProperty** wiąże się z unikatowym identyfikatorem w wystąpieniu formantu. Poniższy kod XAML demonstruje jedno podejście do tworzenia tego powiązania za pomocą szablonu formantu:

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

Podczas definiowania dwóch wystąpień przycisku przy użyciu tego szablonu formantu identyfikator automatyzacji jest ustawiony na unikatowy ciąg zawartości dla formantów w szablonie, jak pokazano w następującym języku XAML:

```xaml
<Button Content="Button1" Style="{StaticResource MyButton}" Width="140"/>
<Button Content="Button2" Style="{StaticResource MyButton}" Width="140"/>
```

### <a name="dynamic-controls"></a>Sterowanie dynamiczne

Jeśli masz formanty, które są tworzone dynamicznie z kodu i nie są tworzone statycznie lub za pośrednictwem szablonów w plikach XAML, należy ustawić właściwości **zawartość** lub **nazwa** formantu. Ta akcja zapewnia, że każdy formant dynamiczny ma unikatową właściwość automatyzacji. Jeśli na przykład masz pole wyboru, które musi być wyświetlane po wybraniu elementu listy, możesz ustawić następujące właściwości, jak pokazano poniżej:

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

## <a name="see-also"></a>Zobacz też

- [Testowanie aplikacji platformy uniwersalnej systemu Windows za pomocą kodowanych testów interfejsu użytkownika](../test/test-uwp-app-with-coded-ui-test.md)
