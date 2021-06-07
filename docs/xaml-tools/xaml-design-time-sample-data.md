---
title: Używanie przykładowych danych czasu projektowania z projektant XAML w Visual Studio
description: Dowiedz się, jak używać przykładowych danych czasu projektowania w języku XAML.
ms.date: 06/01/2021
ms.topic: conceptual
author: alihamie
ms.author: tglee
manager: jmartens
monikerRange: vs-2019
ms.openlocfilehash: 8303e1150db7c12c404e8f67bce52418fbd05b9d
ms.sourcegitcommit: ab5735d64a6ad7aecabf5d6df159888e3246bff5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111433795"
---
# <a name="use-design-time-sample-data-with-the-xaml-designer-in-visual-studio"></a>Używanie przykładowych danych czasu projektowania z projektant XAML w Visual Studio

Niektóre kontrolki, takie jak ListView, ListBox lub DataGrid, są trudne do wizualizacji bez danych. W tym dokumencie przejmiemy nowe podejście, które umożliwia deweloperom pracującym nad projektami **WPF .NET Core** lub **projektami WPF .NET Framework przy** użyciu nowego projektanta włączanie przykładowych danych w tych kontrolkach. 

## <a name="sample-data-feature-basics"></a>Podstawy funkcji przykładowych danych

Przykładowe dane są tylko do wizualizacji w czasie projektowania, co oznacza, że są wyświetlane tylko w projektancie XAML, a nie w uruchomionej aplikacji. W związku z tym jest on stosowany do wersji właściwości ItemsSource w czasie projektowania `d:ItemsSource` . Przykładowe dane muszą działać w przestrzeni nazw czasu projektowania. Aby rozpocząć, dodaj następujące wiersze kodu do nagłówka dokumentu XAML, jeśli jeszcze nie są obecne:

> [!NOTE]
> Odwiedź [stronę Właściwości czasu projektowania XAML,](../xaml-tools/xaml-designtime-data.md) aby dowiedzieć się więcej o właściwościach czasu projektowania w języku XAML.

```xml
xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
mc:Ignorable="d"
```

Po dodaniu przestrzeni nazw możesz użyć elementu , aby włączyć `d:ItemsSource="{d:SampleData}"` przykładowe dane w listView, Listbox lub DataGrid. Na przykład:

```xml
<DataGrid d:ItemsSource="{d:SampleData}"/>
```

[![Przykładowe dane za pomocą dataGrid](media\xaml-sample-data-empty-datagrid.png "Przykładowe dane włączone dla usługi DataGrid")](media\xaml-sample-data-empty-datagrid.png#lightbox)

W tym przykładzie bez projektant XAML `d:ItemsSource="{d:SampleData}"` byłaby pokazywana pusta dataGrid. Zamiast tego teraz `d:SampleData` wyświetla wygenerowane domyślne dane przykładowe.

Domyślnie wyświetlanych jest 5 elementów. Można jednak użyć właściwości **ItemCount,** aby określić liczbę elementów, które mają być wyświetlane. na przykład: `d:ItemsSource="{d:SampleData ItemCount=2}"`

## <a name="sample-data-works-with-datatemplates"></a>Przykładowe dane współpracuje z datatemplates

Przykładowe dane są dostępne dla kontrolek ListBox, ListView lub DataGrid podczas korzystania z szablonów danych. Funkcja Przykładowe dane przeanalizuje element DataTemplate i spróbuje wygenerować dla niego odpowiednie dane. Przykładowe dane będą generowane tylko dla elementów w elementach DataTemplates, które używają powiązań. Przykładowe dane zostaną wygenerowane, nawet jeśli powiązania nie mają jeszcze źródła.
Na przykład:

```xml
<ListView d:ItemsSource="{d:SampleData ItemCount=3}">
     <ListView.ItemTemplate>
        <DataTemplate>
            <StackPanel Orientation="Horizontal">
                <Image Width="50" Source="{Binding ProfilePicture}"/>
                <StackPanel Orientation="Vertical">
                    <TextBlock Text="{Binding FirstName}" Margin="5"/>
                    <Label Content="{Binding LastName}"/>
                </StackPanel>
            </StackPanel>
        </DataTemplate>
    </ListView.ItemTemplate>
</ListView>
```

[![Przykładowe dane ListView z dataTemplate](media\xaml-sample-data-templated-listview.png "Przykładowe dane używane w widoku ListView z dataTemplate")](media\xaml-sample-data-templated-listview.png#lightbox)

## <a name="enable-sample-data-with-suggested-actions"></a>Włączanie przykładowych danych za pomocą sugerowanych akcji

Aby łatwo włączyć lub wyłączyć przykładowe dane dla kontrolki z projektanta, możesz użyć funkcji Sugerowane akcje. Sugerowane akcje to żarówka w projektancie, która pojawia się w prawym górnym rogu po wybraniu kontrolki. Możesz włączyć przykładowe dane, wybierając kontrolkę, klikając żarówkę, a następnie klikając pozycję `Show Sample Data` . Na przykład:

[![Sugerowane akcje przykładowych danych](media\xaml-sample-data-suggested-actions.png "Włączanie przykładowych danych za pomocą sugerowanych akcji")](media\xaml-sample-data-suggested-actions.png#lightbox)

## <a name="sample-data-with-ivalueconverters"></a>Przykładowe dane za pomocą IValueConverters 

Konwertery nie są w pełni obsługiwane przez funkcję Przykładowe dane. Można jednak to zrobić, wykonując jedną lub obie z następujących czynności:
- Upewnij się, że `Convert` funkcja może obsługiwać scenariusz, w którym wartość jest już elementem targetType.

- `ConvertBack`Zaim implementuj funkcję , która przekonwertuje wartość z powrotem na oryginalny typ. 

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Jeśli przykładowe dane nie pokazują niczego lub nie można wyświetlić poprawnego typu, możesz odświeżyć projektanta lub zamknąć i ponownie otworzyć stronę.

Jeśli wystąpi problem, który nie został wymieniony w tej sekcji lub nie można go naprawić przez odświeżenie strony, daj nam znać za pomocą narzędzia Zgłoś [problem.](../ide/how-to-report-a-problem-with-visual-studio.md)

### <a name="requirements"></a>Wymagania

- Przykładowe dane wymagają Visual Studio 2019 w [wersji 16.10](/visualstudio/releases/2019/release-notes-v16.10) lub nowszej.

- Obsługuje projekty klasyczne systemu Windows, które Windows Presentation Foundation (WPF) dla platformy .NET Core lub .NET Framework w przypadku korzystania z nowego projektanta. Aby włączyć nowego projektanta dla programu .NET Framework, przejdź do opcji Narzędzia > Opcje > Environment > w wersji zapoznawczej, wybierz pozycję Nowy projektant XAML WPF dla programu .NET Framework a następnie ponownie uruchom Visual Studio.

## <a name="see-also"></a>Zobacz też

- [Właściwości czasu projektowania XAML](../xaml-tools/xaml-designtime-data.md)
- [Język XAML w aplikacjach WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [Język XAML w aplikacjach platformy UWP](/windows/uwp/xaml-platform/xaml-overview)
- [Język XAML w aplikacjach platformy Xamarin.Forms](/xamarin/xamarin-forms/xaml/)