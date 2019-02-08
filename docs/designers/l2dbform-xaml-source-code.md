---
title: Kod źródłowy L2DBForm.XAML
ms.date: 11/04/2016
ms.topic: sample
ms.assetid: 624e96d4-6d27-4195-8ac2-2f3835f6c57e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b650c65eb81fb087b7783b41065445e1bbea20a0
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55931172"
---
# <a name="l2dbformxaml-source-code"></a>Kod źródłowy L2DBForm.xaml

Ten temat zawiera i opisuje plik źródłowy XAML [powiązanie danych WPF za pomocą LINQ to XML — przykład](../designers/wpf-data-binding-using-linq-to-xml-example.md), *L2DBForm.xaml*.

## <a name="overall-ui-structure"></a>Ogólna struktura interfejsu użytkownika

Podobnie jak w typowej dla projektu WPF, ten plik zawiera jeden element nadrzędny <xref:System.Windows.Window> — element XML skojarzony z klasą pochodną `L2XDBFrom` w `LinqToXmlDataBinding` przestrzeni nazw.

Obszar klienta znajduje się w obrębie <xref:System.Windows.Controls.StackPanel> , otrzymuje światła niebieskim tłem. Ten panel zawiera cztery <xref:System.Windows.Controls.DockPanel> oddzielone sekcje interfejsu użytkownika <xref:System.Windows.Controls.Separator> pasków. Celem tych sekcjach opisano w **uwagi** w [poprzednim temacie](../designers/walkthrough-linqtoxmldatabinding-example.md).

Każda sekcja zawiera etykietę, która identyfikuje go. W pierwszych dwóch sekcjach, ta etykieta jest obrócony o 90 stopni za pośrednictwem <xref:System.Windows.FrameworkElement.LayoutTransform%2A>. Pozostała część sekcji zawiera elementy interfejsu użytkownika, właściwe jest celem tej sekcji: bloki tekstu, pola tekstowe, przyciski i tak dalej. Czasami element podrzędny <xref:System.Windows.Controls.StackPanel> jest używane do dostosowywania tych formantów podrzędnych.

## <a name="window-resource-section"></a>Okno sekcji zasobów

Otwieranie `<Window.Resources>` tagów w wierszu 9 wskazuje początek okna sekcji zasobów. Kończy się ona tagu zamykającego w wierszu 35.

`<ObjectDataProvider>` Znacznik, który obejmuje wiersze 11 do 25, deklaruje <xref:System.Windows.Data.ObjectDataProvider>o nazwie `LoadedBooks`, który używa <xref:System.Xml.Linq.XElement> jako źródło. <xref:System.Xml.Linq.XElement> Jest inicjowany przez analizowanie osadzonego dokumentu XML ( `CDATA` elementu). Należy zauważyć, że biały znak są zachowywane podczas deklarowania osadzonego dokumentu XML, a także, kiedy jest analizowany. Biały znak są zachowywane, ponieważ <xref:System.Windows.Controls.TextBlock> formant, który służy do wyświetlania nieprzetworzonym kodzie XML, nie ma żadnych specjalnych XML funkcji formatowania.

Na koniec <xref:System.Windows.DataTemplate> o nazwie `BookTemplate` jest zdefiniowany w wierszach 28 za pośrednictwem 34. Ten szablon służy do wyświetlania wpisy w **listy książek** sekcji interfejsu użytkownika. Korzysta powiązanie danych oraz LINQ do XML właściwości dynamicznych do pobrania książki identyfikator i Nazwa książki za pośrednictwem następujących przypisań:

```xaml
Text="{Binding Path=Attribute[id].Value}"Text="{Binding Path=Value}"
```

## <a name="data-binding-code"></a>Kod powiązania danych

Oprócz <xref:System.Windows.DataTemplate> element, wiązanie danych jest używany w wielu innych miejscach, w tym pliku.

W otwarcia `<StackPanel>` tagów w wierszu 38 <xref:System.Windows.FrameworkElement.DataContext%2A> tego panelu zostaje ustalona `LoadedBooks` dostawcy danych.

```xaml
DataContext="{Binding Source={StaticResource LoadedBooks}}
```

Ustawianie kontekstu danych umożliwia (w wierszu 46) dla <xref:System.Windows.Controls.TextBlock> o nazwie `tbRawXml` do wyświetlenia nieprzetworzonym kodzie XML przez powiązanie tego dostawcy danych `Xml` właściwości:

```xaml
Text="{Binding Path=Xml}"
```

<xref:System.Windows.Controls.ListBox> w **listy książek** sekcji interfejsu użytkownika w wierszach 58 za pośrednictwem 62, ustawia szablon dla jego elementów wyświetlana `BookTemplate` zdefiniowane w sekcji zasobów okna:

```xaml
ItemTemplate ="{StaticResource BookTemplate}"
```

Następnie w wierszach 59 za pośrednictwem 62 rzeczywiste wartości książek, które są powiązane z tego pola listy:

```xaml
<ListBox.ItemsSource>
    <Binding Path="Elements[{http://www.mybooks.com}book]"/>
</ListBox.ItemsSource>
```

Trzecia sekcja interfejsu użytkownika **Edytuj wybrane książki**, najpierw wiąże <xref:System.Windows.FrameworkElement.DataContext%2A> nadrzędnej <xref:System.Windows.Controls.StackPanel> do aktualnie wybranego elementu z **listy książek** sekcji interfejsu użytkownika (wiersza 82):

```xaml
DataContext="{Binding ElementName=lbBooks, Path=SelectedItem}"
```

Następnie używa powiązanie dwukierunkowe danych, tak aby bieżące wartości książki elementy są wyświetlane i aktualizowane na podstawie dwóch pól tekstowych w tym panelu. Powiązania danych właściwości dynamicznych jest podobny do wiązania danych używanych w `BookTemplate` szablon danych:

```xaml
Text="{Binding Path=Attribute[id].Value}"...Text="{Binding Path=Value}"
```

Ostatnia sekcja interfejsu użytkownika **Dodawanie nowej książki**, nie używa powiązanie danych w jego kod XAML. Zamiast tego powiązania danych znajduje się w jego obsługa kodu w pliku zdarzeń *L2DBForm.xaml.cs*.

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

> [!NOTE]
> Firma Microsoft zaleca, skopiuj poniższy kod poniżej do edytora kodu, takich jak C# Edytor kodu źródłowego w programie Visual Studio, aby numery wierszy będzie można łatwiej śledzić.

### <a name="code"></a>Kod

```xml
<Window x:Class="LinqToXmlDataBinding.L2XDBForm"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:system="clr-namespace:System;assembly=mscorlib"
    xmlns:xlinq="clr-namespace:System.Xml.Linq;assembly=System.Xml.Linq"
    xmlns:local="clr-namespace:LinqToXmlDataBinding"
    Title="WPF Data Binding using LINQ-to-XML" Height="665" Width="500" ResizeMode="NoResize">

    <Window.Resources>
        <!-- Books provider and inline data -->
        <ObjectDataProvider x:Key="LoadedBooks" ObjectType="{x:Type xlinq:XElement}" MethodName="Parse">
            <ObjectDataProvider.MethodParameters>
                <system:String xml:space="preserve">
<![CDATA[
<books xmlns="http://www.mybooks.com">
  <book id="0">book zero</book>
  <book id="1">book one</book>
  <book id="2">book two</book>
  <book id="3">book three</book>
</books>
]]>
                </system:String>
                <xlinq:LoadOptions>PreserveWhitespace</xlinq:LoadOptions>
            </ObjectDataProvider.MethodParameters>
        </ObjectDataProvider>

        <!-- Template for use in Books List listbox. -->
        <DataTemplate x:Key="BookTemplate">
            <StackPanel Orientation="Horizontal">
                <TextBlock Margin="3" Text="{Binding Path=Attribute[id].Value}"/>
                <TextBlock Margin="3" Text="-"/>
                <TextBlock Margin="3" Text="{Binding Path=Value}"/>
            </StackPanel>
        </DataTemplate>
    </Window.Resources>

    <!-- Main visual content container -->
    <StackPanel Background="lightblue" DataContext="{Binding Source={StaticResource LoadedBooks}}">
        <!-- Raw XML display section -->
        <DockPanel Margin="5">
            <Label  Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" FontWeight="Bold">XML
            <Label.LayoutTransform>
                <RotateTransform Angle="90"/>
            </Label.LayoutTransform>
            </Label>
            <TextBlock Name="tbRawXml" Height="200" Background="LightGray" Text="{Binding Path=Xml}" TextTrimming="CharacterEllipsis" />
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- List box to display all books section -->
        <DockPanel Margin="5">
            <Label  Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" FontWeight="Bold">Book List
                <Label.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </Label.LayoutTransform>
            </Label>
            <ListBox Name="lbBooks" Height="200" Width="415" ItemTemplate ="{StaticResource BookTemplate}">
                <ListBox.ItemsSource>
                    <Binding Path="Elements[{http://www.mybooks.com}book]"/>
                </ListBox.ItemsSource>
            </ListBox>
            <Button Margin="5" DockPanel.Dock="Right" Height="30" Width ="130" Content="Remove Selected Book" Click="OnRemoveBook">
            <Button.LayoutTransform>
                <RotateTransform Angle="90"/>
            </Button.LayoutTransform>
            </Button>
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- Edit current selection section -->
        <DockPanel Margin="5">
            <TextBlock Margin="5" Height="30" Width="65" DockPanel.Dock="Right" Background="LightGray" TextWrapping="Wrap" TextAlignment="Center">
                    Changes are live!
                <TextBlock.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </TextBlock.LayoutTransform>
            </TextBlock>
            <StackPanel>
                <Label Width="450" Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" HorizontalAlignment="Left" FontWeight="Bold">Edit Selected Book</Label>
                <StackPanel Margin="1" DataContext="{Binding ElementName=lbBooks, Path=SelectedItem}">
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">ID:</Label>
                        <TextBox Name="editAttributeTextBox" Width="410" Text="{Binding Path=Attribute[id].Value}">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Edit the selected book ID and see it changed.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">Value:</Label>
                        <TextBox Name="editValueTextBox" Width="410" Text="{Binding Path=Value}" Height="25">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Edit the selected book Value and see it changed.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                </StackPanel>
            </StackPanel>
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- Add new book section -->
        <DockPanel Margin="5">
            <Button Margin="5" Height="30" DockPanel.Dock="Right" Click ="OnAddBook">Add Book
                <Button.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </Button.LayoutTransform>
            </Button>
            <StackPanel>
                <Label Width="450" Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" HorizontalAlignment="Left" FontWeight="Bold">Add New Book</Label>
                <StackPanel Margin="1">
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">ID:</Label>
                        <TextBox Name="tbAddID" Width="410">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Enter a book ID and Value pair, then click Add Book.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">Value:</Label>
                        <TextBox Name="tbAddValue" Width="410" Height="25">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="UltraBold" TextAlignment="Center">
                                    <Label>Enter a book ID and Value pair, then click Add Book.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                </StackPanel>
            </StackPanel>
        </DockPanel>
    </StackPanel>
</Window>
```

### <a name="comments"></a>Komentarze

Dla języka C# kodu źródłowego dla obsługi zdarzeń skojarzonych elementów interfejsu użytkownika WPF, zobacz [kod źródłowy L2DBForm.xaml.cs](../designers/l2dbform-xaml-cs-source-code.md).

## <a name="see-also"></a>Zobacz także

- [Przewodnik: LinqToXmlDataBinding example](../designers/walkthrough-linqtoxmldatabinding-example.md)
- [Kod źródłowy L2DBForm.xaml.cs](../designers/l2dbform-xaml-cs-source-code.md)