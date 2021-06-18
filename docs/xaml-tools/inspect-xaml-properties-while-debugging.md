---
title: Sprawdzanie właściwości XAML podczas debugowania | Microsoft Docs
description: Dowiedz się, jak używać narzędzi Live Visual Tree i Live Property Explorer podczas debugowania, aby sprawdzić właściwości XAML i uzyskać widok drzewa elementów interfejsu użytkownika.
ms.custom: SEO-VS-2020
ms.date: 03/02/2021
ms.topic: how-to
ms.assetid: 390edde4-7b8d-4c89-8d69-55106b7e6b11
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- uwp
ms.openlocfilehash: 86310346566e8c937c2769a9fcc9f0d4e98b3ae2
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308444"
---
# <a name="inspect-xaml-properties-while-debugging"></a>Sprawdzanie właściwości XAML podczas debugowania

Widok działającego kodu XAML w czasie rzeczywistym można uzyskać za pomocą drzewa wizualnego na żywo **i** **Eksploratora właściwości na żywo.** Te narzędzia zapewniają widok drzewa elementów interfejsu użytkownika uruchomionej aplikacji XAML i pokazują właściwości środowiska uruchomieniowego dowolnego wybranego elementu interfejsu użytkownika.

Tych narzędzi można używać w następujących konfiguracjach:

|Typ aplikacji|System operacyjny i narzędzia|
|-----------------|--------------------------------|
|Windows Presentation Foundation (4.0 i więcej)|System Windows 7 lub powyższy|
|Aplikacje uniwersalne systemu Windows|Windows 10 i powyższe przy użyciu zestawu [Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk)|

## <a name="look-at-elements-in-the-live-visual-tree"></a>Spojrzenie na elementy w drzewie wizualnym na żywo

Zacznijmy od bardzo prostej aplikacji WPF, która ma widok listy i przycisk. Za każdym razem, gdy klikniesz przycisk, do listy zostanie dodany kolejny element. Elementy z parzystą liczbą mają kolor szary, a elementy z liczbą nieparzystą — żółty.

### <a name="create-the-project"></a>Tworzenie projektu

::: moniker range=">=vs-2019"

1. Utwórz nową aplikację WPF w języku C#**(** File New Project (Nowy projekt), wpisz "C# WPF", wybierz szablon projektu aplikacji WPF, nadaj projektowi nazwę TestXAML, a następnie sprawdź, czy na liście rozwijanej Target Framework (Docelowa framework) jest wyświetlana wartość >  >  **.NET Core 3.1.**   

::: moniker-end

::: moniker range="vs-2017"

1. Utwórz nową aplikację WPF w języku C#**(Utwórz** nowy  >    >  projekt, wpisz "C# WPF" i wybierz pozycję **Aplikacja WPF (.NET Framework)**). Nadaj mu **nazwę TestXAML.**

::: moniker-end

1. Zmień mainWindow.xaml na następujące:

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

1. Dodaj następujący program obsługi poleceń do pliku MainWindow.xaml.cs:

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

1. Skompilowanie projektu i rozpoczęcie debugowania. (Konfiguracją kompilacji musi być debugowanie, a nie wydanie. Aby uzyskać więcej informacji na temat konfiguracji kompilacji, zobacz [Understanding Build Configurations (Opis konfiguracji kompilacji).](../ide/understanding-build-configurations.md)

   Gdy pojawi się okno, w uruchomionej aplikacji powinien zostać wyświetlony pasek narzędzi w aplikacji.

   ::: moniker range=">= vs-2019"
   ![Główne okno aplikacji](../debugger/media/vs-2019/livevisualtree-app.png "LiveVIsualTree-App")
   ::: moniker-end
   ::: moniker range="vs-2017"
   ![Główne okno aplikacji](../debugger/media/livevisualtree-app.png "LiveVIsualTree-App")
   ::: moniker-end

1. Teraz kliknij przycisk **Dodaj element** kilka razy, aby dodać nowe elementy do listy.

### <a name="inspect-xaml-properties"></a>Sprawdzanie właściwości XAML

1. Następnie otwórz okno **Live Visual Tree** (Drzewo wizualne na żywo), klikając lewy przycisk na pasku narzędzi w aplikacji (lub przechodząc do pozycji Debuguj > Windows > Live Visual **Tree).** Po otwarciu przeciągnij go z miejsca dokowania, aby przyjrzeć się temu oknie i oknie Właściwości **na** żywo obok siebie.

1. W **oknie Live Visual Tree (Drzewo wizualne** na żywo) rozwiń węzeł **ContentPresenter.** Powinien on zawierać węzły przycisku i pola listy. Rozwiń pole listy (a następnie **scrollContentPresenter** i **ItemsPresenter),** aby znaleźć elementy pola listy.

   ::: moniker range=">= vs-2019"
   Jeśli nie widzisz węzła **ContentPresenter,** przełącz ikonę Pokaż tylko mój **kod XAML** na pasku narzędzi. Począwszy od Visual Studio 2019 r. w wersji 16.4, widok elementów XAML jest domyślnie uproszczony przy użyciu funkcji Tylko mój kod XAML. Możesz również wyłączyć [to ustawienie w opcjach,](../debugger/general-debugging-options-dialog-box.md) aby zawsze wyświetlać wszystkie elementy XAML.
   ::: moniker-end

   Okno powinno wyglądać tak:

   ::: moniker range=">= vs-2019"
   ![Elementy ListBoxItems w drzewie wizualnym na żywo](../debugger/media/vs-2019/livevisualtree-listboxitems.png "LiveVisualTree-ListBoxItems")
   ::: moniker-end
   ::: moniker range="vs-2017"
   ![Elementy ListBoxItems w drzewie wizualnym na żywo](../debugger/media/livevisualtree-listboxitems.png "LiveVisualTree-ListBoxItems")
   ::: moniker-end

1. Wstecz do okna aplikacji i dodaj jeszcze kilka elementów. W drzewie wizualnym na żywo powinno być wyświetlanych więcej elementów **pola listy.**

1. Teraz przyjrzyjmy się właściwościom jednego z elementów pola listy.

   Wybierz pierwszy element pola listy w drzewie **wizualnym na** żywo i kliknij ikonę Pokaż **właściwości** na pasku narzędzi. Powinien **zostać wyświetlony Eksplorator właściwości** na żywo. Zwróć uwagę, **że pole Zawartość** to "Item1", a pole **Kolor** tła  >   **ma #FFFFFFE0**.

1. Wstecz do live **drzewa wizualnego** i wybierz drugi element pola listy. Eksplorator **właściwości na żywo**  powinien pokazywać, że pole Zawartość ma wartość "Item2", a pole Kolor tła  >   **jest #FFD3D3D3** (w zależności od motywu).

   > [!NOTE]
   > Żółte obramowanie wokół właściwości w Eksploratorze właściwości **na** żywo oznacza, że wartość właściwości jest ustawiana za pomocą powiązania, takiego jak `Color = {BindingExpression}` . Zielone obramowanie oznacza, że wartość jest ustawiana przy użyciu zasobu, takiego jak `Color = {StaticResource MyBrush}` .

   Rzeczywista struktura kodu XAML zawiera wiele elementów, które prawdopodobnie nie są bezpośrednio zainteresowane, a jeśli nie znasz dobrze kodu, może być trudno nawigować po drzewie, aby znaleźć to, czego szukasz. Dlatego drzewo **wizualne na** żywo ma kilka sposobów, które umożliwiają użycie interfejsu użytkownika aplikacji w celu znalezienia elementu, który chcesz zbadać.

   ::: moniker range=">= vs-2019"
   **Wybierz element w uruchomionej aplikacji**. Ten tryb można włączyć po wybraniu przycisku po lewej stronie na pasku **narzędzi live drzewa wizualnego.** W tym trybie można wybrać element interfejsu użytkownika w aplikacji, a dynamiczne drzewo wizualne **(i** Podgląd właściwości na żywo **)** są automatycznie aktualizowane, aby pokazać węzeł w drzewie odpowiadającym temu elementowi i jego właściwości. Począwszy od Visual Studio 2019 w wersji 16.4, można skonfigurować [zachowanie wyboru elementu](../debugger/general-debugging-options-dialog-box.md).

   **Wyświetlanie układów definiowania układu w uruchomionej aplikacji.** Ten tryb można włączyć po wybraniu przycisku, który znajduje się natychmiast po prawej stronie przycisku Włącz wybór. Gdy  jest w pozycji Wyświetlanie układu definiowania układu, w oknie aplikacji są wyświetlane linie poziome i pionowe wzdłuż granic wybranego obiektu, dzięki czemu można zobaczyć, do czego jest wyrównany, a także prostokąty przedstawiające marginesy. Na przykład włącz zarówno pozycję **Wybierz element,** jak i **układ** Wyświetlanie, a następnie wybierz blok **tekstowy** Dodaj element w aplikacji. Węzeł bloków tekstu powinien  być wyświetlony w drzewie wizualnym na żywo oraz we właściwościach bloku tekstu w Podglądzie właściwości na **żywo,** a także linii poziomych i pionowych na granicach bloku tekstu.

   ![LivePropertyViewer w displaylayout](../debugger/media/vs-2019/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer-DisplayLayout")

   **Podgląd wyboru**. Możesz włączyć ten tryb, wybierając trzeci przycisk z lewej strony na pasku narzędzi live drzewa wizualnego. W tym trybie jest przedstawiany kod XAML, w którym zadeklarowano element, jeśli masz dostęp do kodu źródłowego aplikacji. Wybierz **pozycję Wybierz element** i wybierz **pozycję** Podgląd, a następnie wybierz przycisk w naszej aplikacji testowej. Plik MainWindow.xaml zostanie otwarty w Visual Studio i kursor zostanie umieszczony w wierszu, w którym zdefiniowano przycisk.
   ::: moniker-end

   ::: moniker range="vs-2017"
   **Włącz wybór w uruchomionej aplikacji.** Ten tryb można włączyć po wybraniu przycisku po lewej stronie na pasku **narzędzi live drzewa wizualnego.** W tym trybie można wybrać element interfejsu użytkownika w aplikacji, a dynamiczne drzewo wizualne **(i** Podgląd właściwości na żywo **)** są automatycznie aktualizowane, aby pokazać węzeł w drzewie odpowiadającym temu elementowi i jego właściwości.

   **Wyświetlanie układów definiowania układu w uruchomionej aplikacji.** Ten tryb można włączyć po wybraniu przycisku, który znajduje się natychmiast po prawej stronie przycisku Włącz wybór. Gdy  jest w pozycji Wyświetlanie układu definiowania układu, w oknie aplikacji są wyświetlane linie poziome i pionowe wzdłuż granic wybranego obiektu, dzięki czemu można zobaczyć, do czego jest wyrównany, a także prostokąty przedstawiające marginesy. Na przykład włącz opcję **Włącz wybór** i **Układ wyświetlania,** a następnie wybierz blok **tekstowy** Dodaj element w aplikacji. Węzeł bloków tekstu powinien  być wyświetlony w drzewie wizualnym na żywo oraz we właściwościach bloku tekstu w Podglądzie właściwości na **żywo,** a także linii poziomych i pionowych na granicach bloku tekstu.

   ![LivePropertyViewer w displaylayout](../debugger/media/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer-DisplayLayout")

   **Podgląd wyboru**. Możesz włączyć ten tryb, wybierając trzeci przycisk z lewej strony na pasku narzędzi live drzewa wizualnego. W tym trybie jest przedstawiany kod XAML, w którym zadeklarowano element, jeśli masz dostęp do kodu źródłowego aplikacji. Wybierz **pozycję Włącz wybór** i **Podgląd** zaznaczenia, a następnie wybierz przycisk w naszej aplikacji testowej. Plik MainWindow.xaml zostanie otwarty w Visual Studio i kursor zostanie umieszczony w wierszu, w którym zdefiniowano przycisk.
   ::: moniker-end

## <a name="use-xaml-tools-with-running-applications"></a>Używanie narzędzi XAML z uruchomionymi aplikacjami

Tych narzędzi XAML można używać nawet wtedy, gdy nie masz kodu źródłowego. Po dołączeniu do uruchomionej aplikacji XAML możesz użyć działającego drzewa **wizualnego** również w elementach interfejsu użytkownika tej aplikacji. Oto przykład użycia tej samej aplikacji testowej WPF, która została użyta wcześniej.

1. Uruchom aplikację **TestXaml** w konfiguracji wydania. Nie można dołączyć do procesu, który jest uruchomiony w konfiguracji **debugowania.**

2. Otwórz drugie wystąpienie klasy i Visual Studio **pozycję Debuguj, > dołącz do procesu.** Znajdź **TestXaml.exe** na liście dostępnych procesów, a następnie kliknij pozycję **Dołącz.**

3. Aplikacja zacznie działać.

4. W drugim wystąpieniu programu otwórz Visual Studio **Wizualne** **(Debugowanie**> Windows > Live Visual Tree). Powinny zostać wyświetlony elementy interfejsu użytkownika **TestXaml** i powinno być możliwe manipulowanie nimi tak jak podczas bezpośredniego debugowania aplikacji.

## <a name="see-also"></a>Zobacz też

[Pisanie i debugowanie uruchomionego kodu XAML za pomocą Przeładowywanie kodu XAML na gorąco](xaml-hot-reload.md)
