---
title: Kod źródłowy L2DBForm.xaml
ms.date: 11/04/2016
ms.topic: sample
ms.assetid: 624e96d4-6d27-4195-8ac2-2f3835f6c57e
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41796664d5456876edff81662cbab44edf7a82f2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72635289"
---
# <a name="l2dbformxaml-source-code"></a>Kod źródłowy L2DBForm.xaml

Ten temat zawiera i opisuje plik źródłowy XAML dla [powiązania danych WPF przy użyciu LINQ to XML przykład](../designers/wpf-data-binding-using-linq-to-xml-example.md) *kod źródłowy L2DBForm. XAML*.

## <a name="overall-ui-structure"></a>Ogólna struktura interfejsu użytkownika

Podobnie jak w przypadku projektu WPF, ten plik zawiera jeden element nadrzędny, <xref:System.Windows.Window> elementu XML skojarzonego z klasą pochodną `L2XDBFrom` w przestrzeni nazw `LinqToXmlDataBinding`.

Obszar klienta jest zawarty w <xref:System.Windows.Controls.StackPanel>, w którym znajduje się jasne niebieskie tło. Ten panel zawiera cztery <xref:System.Windows.Controls.DockPanel> sekcje interfejsu użytkownika oddzielone <xref:System.Windows.Controls.Separator> słupków. Przeznaczenie tych sekcji zostało opisane w **uwagach** w [poprzednim temacie](../designers/walkthrough-linqtoxmldatabinding-example.md).

Każda sekcja zawiera etykietę identyfikującą ją. W pierwszych dwóch sekcjach Ta etykieta jest obracana o 90 stopni przy użyciu <xref:System.Windows.FrameworkElement.LayoutTransform%2A>. Pozostała część sekcji zawiera elementy interfejsu użytkownika odpowiednie do przeznaczenia tej sekcji: bloki tekstu, pola tekstowe, przyciski i tak dalej. Czasami podrzędny <xref:System.Windows.Controls.StackPanel> jest używany do wyrównywania tych formantów podrzędnych.

## <a name="window-resource-section"></a>Sekcja zasobów okna

Otwierając tag `<Window.Resources>` w wierszu 9 wskazuje początek sekcji zasobów okna. Jest ona kończąca się tagiem zamykającym w wierszu 35.

Znacznik `<ObjectDataProvider>`, który obejmuje wiersze od 11 do 25, deklaruje <xref:System.Windows.Data.ObjectDataProvider> o nazwie `LoadedBooks`, który używa <xref:System.Xml.Linq.XElement> jako źródła. @No__t_0 jest inicjowany przez analizowanie osadzonego dokumentu XML (`CDATA` elementu). Należy zauważyć, że biały znak jest zachowywany podczas deklarowania osadzonego dokumentu XML, a także podczas analizy. Biały znak jest zachowywany, ponieważ kontrolka <xref:System.Windows.Controls.TextBlock>, która jest używana do wyświetlania nieprzetworzonego kodu XML, nie ma specjalnych funkcji formatowania XML.

Na koniec <xref:System.Windows.DataTemplate> o nazwie `BookTemplate` jest zdefiniowany w wierszach od 28 do 34. Ten szablon służy do wyświetlania wpisów w sekcji interfejsu użytkownika **listy książek** . Używa on powiązań danych i LINQ to XML właściwości dynamiczne, aby pobrać identyfikator i nazwę książki przy użyciu następujących przypisań:

```xaml
Text="{Binding Path=Attribute[id].Value}"Text="{Binding Path=Value}"
```

## <a name="data-binding-code"></a>Kod powiązania danych

Oprócz elementu <xref:System.Windows.DataTemplate>, powiązanie danych jest używane w wielu innych miejscach w tym pliku.

W tagu `<StackPanel>` otwierającym w wierszu 38 Właściwość <xref:System.Windows.FrameworkElement.DataContext%2A> tego panelu jest ustawiona na dostawcę danych `LoadedBooks`.

```xaml
DataContext="{Binding Source={StaticResource LoadedBooks}}
```

Ustawienie kontekstu danych sprawia, że jest to możliwe (w wierszu 46) dla <xref:System.Windows.Controls.TextBlock> o nazwie `tbRawXml` do wyświetlania nieprzetworzonego kodu XML przez powiązanie z właściwością `Xml` tego dostawcy danych:

```xaml
Text="{Binding Path=Xml}"
```

@No__t_0 w sekcji interfejsu użytkownika **listy książek** , w wierszach od 58 do 62, ustawia szablon dla elementów wyświetlanych na `BookTemplate` zdefiniowany w sekcji zasobów okna:

```xaml
ItemTemplate ="{StaticResource BookTemplate}"
```

Następnie w wierszach od 59 do 62 rzeczywiste wartości ksiąg są powiązane z tym polem listy:

```xaml
<ListBox.ItemsSource>
    <Binding Path="Elements[{http://www.mybooks.com}book]"/>
</ListBox.ItemsSource>
```

Trzecia sekcja interfejsu użytkownika, **Edytuj wybraną książkę**, najpierw wiąże <xref:System.Windows.FrameworkElement.DataContext%2A> nadrzędnej <xref:System.Windows.Controls.StackPanel> z aktualnie wybranym elementem w sekcji z poziomu interfejsu użytkownika **listy książek** (wiersz 82):

```xaml
DataContext="{Binding ElementName=lbBooks, Path=SelectedItem}"
```

Następnie używa dwukierunkowego wiązania danych, dzięki czemu bieżące wartości elementów książki są wyświetlane do i aktualizowane z, dwa pola tekstowe na tym panelu. Powiązanie danych z właściwościami dynamicznymi jest podobne do powiązania danych używanego w szablonie danych `BookTemplate`:

```xaml
Text="{Binding Path=Attribute[id].Value}"...Text="{Binding Path=Value}"
```

Ostatnia sekcja interfejsu użytkownika, **Dodaj nową książkę**, nie używa powiązania danych w kodzie XAML. Zamiast tego powiązanie danych znajduje się w kodzie obsługi zdarzeń w pliku *L2DBForm.XAML.cs*.

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

> [!NOTE]
> Zalecamy skopiowanie poniższego kodu do edytora kodu, takiego jak edytor kodu C# źródłowego w programie Visual Studio, dzięki czemu numery wierszy będą łatwiejsze do śledzenia.

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

W przypadku C# kodu źródłowego dla programów obsługi zdarzeń skojarzonych z elementami interfejsu użytkownika WPF zobacz [kod źródłowy L2DBForm.XAML.cs](../designers/l2dbform-xaml-cs-source-code.md).

## <a name="see-also"></a>Zobacz także

- [Przewodnik: elementu LinqToXmlDataBinding — przykład](../designers/walkthrough-linqtoxmldatabinding-example.md)
- [Kod źródłowy L2DBForm.xaml.cs](../designers/l2dbform-xaml-cs-source-code.md)