---
title: Sprawdzanie właściwości XAML podczas debugowania | Dokumentacja firmy Microsoft
ms.date: 03/06/2017
ms.topic: conceptual
ms.assetid: 390edde4-7b8d-4c89-8d69-55106b7e6b11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: d5b04a64ea75458d23e64e83a405a103ae70a100
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62906073"
---
# <a name="inspect-xaml-properties-while-debugging"></a>Sprawdzanie właściwości XAML podczas debugowania
Możesz uzyskać wgląd w czasie rzeczywistym uruchamianie kodu XAML za pomocą **dynamiczne drzewo wizualne** i **Eksplorator właściwości na żywo**. Te narzędzia umożliwiają widok drzewa elementów interfejsu użytkownika w uruchomionej aplikacji XAML i dowiesz się, właściwości środowiska uruchomieniowego dowolnego elementu interfejsu użytkownika, którą wybierzesz.

Można użyć tych narzędzi w następujących konfiguracji:

|Typ aplikacji|System operacyjny i narzędzia|
|-----------------|--------------------------------|
|Aplikacje Windows Presentation Foundation (4.0 i nowsze)|Windows 7 i nowsze wersje|
|Universal Windows apps|System Windows 10 i nowsze wersje z [systemu Windows 10 SDK](https://dev.windows.com/en-us/downloads/windows-10-sdk)|

## <a name="looking-at-elements-in-the-live-visual-tree"></a>Patrząc elementów w dynamicznym drzewie wizualnym
Zacznijmy od bardzo prostej aplikacji WPF, która zawiera widok listy i przycisk. Za każdym razem, gdy użytkownik kliknie przycisk, inny element zostanie dodany do listy. Parzystych elementy mają kolor szary, a nieparzystych elementów mają kolor na żółty.

Utwórz nową C# aplikacji WPF (Plik > Nowy > Projekt, następnie wybierz pozycję C# i Znajdź aplikację WPF). Nadaj mu nazwę **TestXAML**.

Zmień MainWindow.xaml następujące czynności:

```xaml
<Window x:Class="TestXAML.MainWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    xmlns:local="clr-namespace:TestXAML"
    mc:Ignorable="d"
    Title="MainWindow" Height="350" Width="525">
    <Grid>
        <Button x:Name="button" Background="LightBlue" Content="Add Item" HorizontalAlignment="Left" Margin="216,206,0,0" VerticalAlignment="Top" Width="75" Click="button_Click"/>
        <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="100" VerticalAlignment="Top" Width="100" Margin="205,80,0,0"/>
    </Grid>
</Window>
```

Dodaj następujący program obsługi poleceń do pliku MainWindow.xaml.cs:

```csharp
int count;

private void button_Click(object sender, RoutedEventArgs e)
{
    ListBoxItem item = new ListBoxItem();
    item.Content = "Item" + ++count;
    if (count % 2 == 0)
    {
        item.Background = Brushes.LightGray;
    }
    else
    {
        item.Background = Brushes.LightYellow;
    }
    listBox.Items.Add(item);
}
```

Skompiluj projekt, a następnie rozpocząć debugowanie. (Konfiguracja kompilacji musi być Debug i Release nie. Aby uzyskać więcej informacji o konfiguracjach kompilacji, zobacz [ogólne informacje o konfiguracjach kompilacji](../ide/understanding-build-configurations.md).)

Po wyświetleniu okna, kliknij przycisk **elementu Dodawanie** przycisk kilka razy. Powinien zostać wyświetlony podobny do poniższego:

![Okno główne aplikacji](../debugger/media/livevisualtree-app.png "LiveVIsualTree aplikacji")

Teraz otworzyć **dynamiczne drzewo wizualne** okna (**Debuguj > Windows > dynamiczne drzewo wizualne**, lub znaleźć wzdłuż lewej części IDE). Przeciągnij od położenia dokowania, dzięki czemu można przyjrzymy się to okno i **właściwości na żywo** oknie obok siebie. W **dynamiczne drzewo wizualne** okna, rozwiń węzeł **ContentPresenter** węzła. Powinien on zawierać węzły przycisk i pole listy. Rozwiń pole listy (i następnie **ScrollContentPresenter** i **ItemsPresenter**) można znaleźć na liście pola wyboru. Okno powinno wyglądać następująco:

![Obiekty ListBoxItem w dynamicznym drzewie wizualnym obiekcie](../debugger/media/livevisualtree-listboxitems.png "LiveVisualTree ListBoxItems")

Wróć do okna aplikacji i dodaj kilka więcej elementów. Powinien zostać wyświetlony więcej elementów pola listy są wyświetlane w **dynamiczne drzewo wizualne**.

Teraz Przyjrzyjmy się właściwości jednego z elementów pola listy. Wybierz pierwszy element listy w polu, w **dynamiczne drzewo wizualne** i kliknij przycisk **Pokaż właściwości** ikonę na pasku narzędzi. **Eksplorator właściwości na żywo** powinna zostać wyświetlona. Należy pamiętać, że **zawartości** pole jest "Item1 —", a **tła** pole jest **#FFFFFFE0** (jasny żółty). Wróć do **dynamiczne drzewo wizualne** i wybierz drugi element listy w polu. **Eksplorator właściwości na żywo** powinno pokazać, że **zawartości** pole jest "Item2 —", a **tła** pole jest **#FFD3D3D3** (światła szare ).

Rzeczywiste struktury XAML ma wiele elementów, które prawdopodobnie nie jesteś zainteresowany bezpośrednio, a jeśli nie znasz dobrze kod może mieć twarde czasie, przechodząc drzewa, aby dowiedzieć się, czego szukasz. Więc **dynamiczne drzewo wizualne** ma kilka sposobów umożliwiające korzystanie z interfejsu użytkownika aplikacji w ułatwią znalezienie element, który chcesz zbadać.

**Włącz zaznaczanie w uruchomionej aplikacji**. Możesz włączyć ten tryb, po wybraniu skrajnie po lewej stronie przycisku na **dynamiczne drzewo wizualne** paska narzędzi. W tym trybie można wybrać elementu interfejsu użytkownika w aplikacji, a **dynamiczne drzewo wizualne** (i **podglądu na żywo właściwość**) automatycznie aktualizuje, aby wyświetlić węzeł w drzewie odpowiadający tego elementu i jego właściwości.

**Wyświetl moduły definiowania układu kodu w uruchomionej aplikacji**. Po wybraniu przycisku, który jest od razu po prawej stronie przycisku Włącz wybór można włączyć ten tryb. Gdy **Wyświetl moduły definiowania układu kodu** jest włączona, sprawia, że okna aplikacji wyświetlić poziome i pionowe linie wzdłuż granice wybranego obiektu, dzięki czemu można zobaczyć, co powoduje wyrównanie, a także prostokąty marginesy. Na przykład włączyć zarówno **Włącz zaznaczanie** i **Układ wyświetlania** na i wybierz **elementu Dodawanie** blok tekstu w aplikacji. Powinien zostać wyświetlony w węźle blok tekstu **dynamiczne drzewo wizualne** i tekst blok właściwości w **podglądu na żywo właściwość**, a także poziome i pionowe wierszach zakresem bloku tekstu.

![LivePropertyViewer w DisplayLayout](../debugger/media/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer DisplayLayout")

**Wyświetl podgląd zaznaczenia**. W tym trybie można włączyć, zaznaczając trzeci przycisk z lewej strony, na pasku narzędzi dynamiczne drzewo wizualne. W tym trybie pokazuje XAML, w którym element został zadeklarowany, jeśli masz dostęp do kodu źródłowego aplikacji. Wybierz **Włącz zaznaczanie** i **podgląd zaznaczenia**, a następnie wybierz przycisk w naszej aplikacji testowych. Pliku MainWindow.xaml, który zostanie otwarty w programie Visual Studio i znajduje się kursor w wierszu, jest definiowana przycisku.

## <a name="using-xaml-tools-with-running-applications"></a>Używanie narzędzi XAML z uruchamiania aplikacji
Można użyć tych narzędzi XAML, nawet wtedy, gdy nie masz kodu źródłowego. Po dołączeniu do uruchomionej aplikacji XAML, możesz użyć **dynamiczne drzewo wizualne** od elementów interfejsu użytkownika w tej aplikacji za. Oto przykład, przy użyciu tej samej aplikacji WPF testu, którego używaliśmy wcześniej.

1. Rozpocznij **TestXaml** aplikacji w konfiguracji wydania. Nie można dołączyć do procesu, który jest uruchomiony w **debugowania** konfiguracji.

2. Otwórz drugie wystąpienie programu Visual Studio, a następnie kliknij przycisk **Debuguj > Dołącz do procesu**. Znajdź **TestXaml.exe** na liście dostępnych procesów, a następnie kliknij przycisk **Dołącz**.

3. Uruchamiania aplikacji.

4. W drugim wystąpieniu programu Visual Studio, otwórz **dynamiczne drzewo wizualne** (**Debuguj > Windows > dynamiczne drzewo wizualne**). Powinien zostać wyświetlony **TestXaml** elementy interfejsu użytkownika, a powinien móc manipulować nimi, jak podczas debugowania aplikacji bezpośrednio.
