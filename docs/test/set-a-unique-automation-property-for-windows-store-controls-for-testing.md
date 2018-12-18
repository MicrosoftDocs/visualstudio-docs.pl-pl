---
title: Ustawianie unikatowej właściwości automatyzacji dla kontrolek platformy UWP przeznaczonych do testowania
ms.date: 05/31/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- uwp
author: gewarren
ms.openlocfilehash: 1cc8986c3101bb2048e0cd4ace739974031344ed
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2018
ms.locfileid: "52894784"
---
# <a name="set-a-unique-automation-property-for-uwp-controls-for-testing"></a>Ustawianie unikatowej właściwości automatyzacji dla kontrolek platformy uniwersalnej systemu Windows do testowania

Jeśli chcesz uruchomić kodowane testy interfejsu użytkownika dla aplikacji platformy uniwersalnej systemu Windows oparte na XAML, każda kontrolka musi posiadać unikatowej właściwości automatyzacji. Możesz przypisać unikatowej właściwości automatyzacji na podstawie typu kontrolki XAML w aplikacji.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="static-xaml-definition"></a>Statyczne definicji XAML

Aby określić unikatowej właściwości automatyzacji dla formantu, który jest zdefiniowany w pliku XAML, można ustawić **AutomationProperties.AutomationId** lub **AutomationProperties.Name** jawnie lub niejawnie, jak pokazano w przykładach. Jedną z tych wartości ustawienia zapewnia kontrolę unikatowej właściwości automatyzacji, który może służyć do identyfikowania formantu, tworząc kodowanego interfejsu użytkownika testowego, nagrywanie akcji.

### <a name="set-the-property-implicitly"></a>Ustaw właściwość niejawnie

Ustaw **AutomationProperties.AutomationId** do **ButtonX** przy użyciu **nazwa** właściwości w XAML dla formantu.

```xaml
<Button Name="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />
```

Ustaw **AutomationProperties.Name** do **ButtonY** przy użyciu **zawartości** właściwości w XAML dla formantu.

```xaml
<Button Content="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />
```

### <a name="set-the-property-explicitly"></a>Ustaw jawnie właściwość

Ustaw **AutomationProperties.AutomationId** do **ButtonX** jawnie w XAML dla formantu.

```xaml
<Button AutomationProperties.AutomationId="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />
```

Ustaw **AutomationProperties.Name** do **ButtonY** jawnie w XAML dla formantu.

```xaml
<Button AutomationProperties.Name="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />
```

## <a name="assign-unique-names"></a>Przypisać unikatowe nazwy

W programie Blend for Visual Studio, można wybrać opcję, aby przypisać unikalną nazwę do elementów interaktywnych, takich jak przyciski, pola listy, pola kombi i pól tekstowych, które zawiera unikatowe wartości kontrolki **AutomationProperties.Name**.

Aby przypisać unikatowe nazwy istniejących formantów, zaznacz **narzędzia** > **nadawać nazwy elementom interaktywnym**.

![Nazwij elementy interaktywne w programie Blend for Visual Studio](../test/media/cuit_windowsstoreproperty_blend_1.png)

Automatycznie oferowanie unikatowe nazwy nowych formantów, które można dodać, wybierz **narzędzia** > **opcje** otworzyć **opcje** okna dialogowego. Wybierz **projektanta XAML** , a następnie wybierz **automatycznie nazwij elementy interakcyjne przy tworzeniu**. Wybierz **OK** aby zamknąć okno dialogowe.

## <a name="use-a-data-template"></a>Korzystanie z szablonu danych

Można zdefiniować przy użyciu prostego szablonu **właściwości ItemTemplate** do powiązania wartości w polu listy zmiennych:

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

Można również użyć szablonu z **ItemContainerStyle** do powiązania wartości do zmiennych:

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

Dla obu tych przykładów można następnie zastąpić **ToString()** metody **właściwości ItemSource**, jak pokazano w przykładzie kodu, który następuje po użyciu. Ten kod zapewniają, że **AutomationProperties.Name** wartość jest ustawiona i jest unikatowa, ponieważ nie można ustawić unikatowej właściwości automatyzacji dla każdego elementu listy powiązanych z danymi za pomocą powiązania. Ustawiając unikatową wartość dla **Properties.Name automatyzacji** w tym przypadku jest wystarczająca.

> [!NOTE]
> W ten sposób zawartość wewnętrzny elementu listy, można również ustawić na ciąg w klasie pracowników za pośrednictwem powiązania. Jak pokazano w przykładzie, formant przycisku wewnątrz każdego elementu listy jest przypisany identyfikator unikatowy automatyzacji, czyli identyfikatora pracownika.

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

## <a name="use-a-control-template"></a>Korzystanie z szablonu kontrolki

Tak, aby każde wystąpienie określonego typu uzyskuje unikatowej właściwości automatyzacji, jeśli jest zdefiniowana w kodzie, można użyć szablonu kontrolki. Tworzenie szablonu, aby **AutomationProperty** wiąże Unikatowy identyfikator w wystąpienia formantu. Następujące XAML demonstruje jedno z podejść do utworzenia powiązania z szablonu kontrolki:

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

Podczas definiowania dwa wystąpienia przy użyciu tego szablonu kontrolki przycisku identyfikator usługi automation jest równa unikatowy ciąg tekstowy zawartości dla formantów w szablonie, jak pokazano w poniższym XAML:

```xaml
<Button Content="Button1" Style="{StaticResource MyButton}" Width="140"/>
<Button Content="Button2" Style="{StaticResource MyButton}" Width="140"/>
```

### <a name="dynamic-controls"></a>Kontrolek dynamicznych

Jeśli masz formantów, które są tworzone dynamicznie w kodzie i nieutworzonych statycznie lub za pomocą szablonów w plikach XAML, musisz ustawić **zawartości** lub **nazwa** właściwości formantu. Ta akcja gwarantuje, że każda kontrolka dynamiczna ma unikatowej właściwości automatyzacji. Na przykład jeśli pole wyboru, które można wyświetlić, wybierz element listy, można ustawić te właściwości, jak pokazano poniżej:

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

- [Testowanie aplikacji platformy uniwersalnej systemu Windows za pomocą kodowanych testów interfejsu użytkownika](../test/test-uwp-app-with-coded-ui-test.md)
