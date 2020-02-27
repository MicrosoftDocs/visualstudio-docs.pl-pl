---
title: Sprawdź właściwości XAML podczas debugowania | Microsoft Docs
ms.date: 11/12/2019
ms.topic: conceptual
ms.assetid: 390edde4-7b8d-4c89-8d69-55106b7e6b11
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.technology: vs-ide-debug
ms.workload:
- uwp
ms.openlocfilehash: 36246f959aa49e49aa84defc203075f163c67118
ms.sourcegitcommit: 9de7d25056da59df0941508c80c0b12766ba6580
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "77706412"
---
# <a name="inspect-xaml-properties-while-debugging"></a>Sprawdzanie właściwości XAML podczas debugowania 

Możesz uzyskać widok działającego kodu XAML w czasie rzeczywistym za pomocą **aktywnego drzewa wizualnego** i **Eksploratora właściwości na żywo**. Te narzędzia udostępniają widok drzewa elementów interfejsu użytkownika uruchomionej aplikacji XAML i pokazują właściwości środowiska uruchomieniowego każdego z wybranych elementów interfejsu użytkownika.

Można używać tych narzędzi w następujących konfiguracjach:

|Typ aplikacji|System operacyjny i narzędzia|
|-----------------|--------------------------------|
|Aplikacje Windows Presentation Foundation (4,0 i nowsze)|System Windows 7 lub nowszy|
|Aplikacje uniwersalne systemu Windows|System Windows 10 lub nowszy z [zestawem SDK systemu Windows 10](https://dev.windows.com/downloads/windows-10-sdk)|

## <a name="look-at-elements-in-the-live-visual-tree"></a>Poszukaj elementów w dynamicznym drzewie wizualnym

Zacznijmy od bardzo prostej aplikacji WPF, która zawiera widok listy i przycisk. Za każdym razem, gdy klikniesz przycisk, kolejny element zostanie dodany do listy. Elementy oznaczone parzyste są kolorami szarymi, a elementy o numerach nieparzystych są kolorem żółtym.

### <a name="create-the-project"></a>Tworzenie projektu

1. Utwórz C# nową aplikację WPF (**plik** > **nowym** > **projekcie**, a następnie wpisz ciągC# "WPF" i wybierz pozycję **Aplikacja WPF (.NET Core)** lub **Aplikacja WPF (.NET Framework)** . Nadaj mu nazwę **TestXaml**.

1. Zmień MainWindow. XAML na następujący:

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

1. Dodaj następującą procedurę obsługi polecenia do pliku MainWindow.xaml.cs:

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

1. Skompiluj projekt, a następnie rozpocząć debugowanie. (Konfiguracja kompilacji musi być debugowana, nie wersja. Aby uzyskać więcej informacji o konfiguracjach kompilacji, zobacz [Opis konfiguracji kompilacji](../ide/understanding-build-configurations.md).)

   Po wyświetleniu okna powinien pojawić się pasek narzędzi w aplikacji w działającej aplikacji.

   ::: moniker range=">= vs-2019" 
   ![Główne okno aplikacji](../debugger/media/vs-2019/livevisualtree-app.png "LiveVIsualTree — aplikacja")
   ::: moniker-end
   ::: moniker range="vs-2017" 
   ![Główne okno aplikacji](../debugger/media/livevisualtree-app.png "LiveVIsualTree — aplikacja")
   ::: moniker-end

1. Teraz kliknij przycisk **Dodaj element** kilka razy, aby dodać nowe elementy do listy.

### <a name="inspect-xaml-properties"></a>Sprawdzanie właściwości XAML

1. Następnie otwórz okno **dynamiczne drzewo wizualne** , klikając przycisk z lewej strony na pasku narzędzi w aplikacji (lub przechodząc do **debugowania > Windows > dynamicznym drzewie wizualnym**). Po jej otwarciu przeciągnij ją z pozycji dokującej, aby można było zobaczyć to okno i okno **właściwości na żywo** obok siebie.

1. W oknie **dynamiczne drzewo wizualne** rozwiń węzeł **ContentPresenter** . Powinien zawierać węzły dla przycisku i pola listy. Rozwiń pole listy (a następnie **ScrollContentPresenter** i **ItemsPresenter**), aby znaleźć elementy pola listy.

   ::: moniker range=">= vs-2019" 
   Jeśli nie widzisz węzła **ContentPresenter** , przełącz ikonę **Pokaż tylko mój kod XAML** na pasku narzędzi. Począwszy od programu Visual Studio 2019 w wersji 16,4, widok elementów XAML jest domyślnie uproszczony za pomocą funkcji tylko mój kod XAML. [To ustawienie](../debugger/general-debugging-options-dialog-box.md) można także wyłączyć w opcjach, aby zawsze wyświetlać wszystkie elementy XAML.
   ::: moniker-end

   Okno powinno wyglądać następująco:

   ::: moniker range=">= vs-2019" 
   ![ListBoxItems w dynamicznym drzewie wizualnym](../debugger/media/vs-2019/livevisualtree-listboxitems.png "LiveVisualTree-ListBoxItems")
   ::: moniker-end
   ::: moniker range="vs-2017" 
   ![ListBoxItems w dynamicznym drzewie wizualnym](../debugger/media/livevisualtree-listboxitems.png "LiveVisualTree-ListBoxItems")
   ::: moniker-end

1. Wróć do okna aplikacji i Dodaj kilka innych elementów. W **dynamicznym drzewie wizualnym**powinny być widoczne więcej elementów pola listy.

1. Teraz przyjrzyjmy się właściwościom jednego z elementów pola listy.

   Wybierz pierwszy element pola listy w **dynamicznym drzewie wizualnym** i kliknij ikonę **Pokaż właściwości** na pasku narzędzi. Powinien pojawić się **Eksplorator właściwości na żywo** . Należy pamiętać, że pole **Content** ma wartość "Item1 —", a pole **koloru** > **tła** jest **#FFFFFFE0**.
   
1. Wróć do **aktywnego drzewa wizualnego** i wybierz drugi element pola listy. **Eksplorator właściwości na żywo** powinien pokazać, że pole **Content** ma wartość "Item2 —", a pole **koloru** > **tła** jest **#FFD3D3D3** (w zależności od motywu).

   > [!NOTE]
   > Żółte obramowanie wokół właściwości w **Eksploratorze właściwości na żywo** oznacza, że wartość właściwości jest ustawiana za pośrednictwem powiązania, takiego jak `Color = {BindingExpression}`. Zielona krawędź oznacza, że wartość jest ustawiana za pomocą zasobu, takiego jak `Color = {StaticResource MyBrush}`.

   Rzeczywista struktura języka XAML zawiera wiele elementów, które prawdopodobnie nie są bezpośrednio zainteresowane. Jeśli nie znasz dobrze kodu, być może masz czas, w którym możesz uzyskać informacje o tym, czego szukasz. Tak więc **dynamiczne drzewo wizualne** zawiera kilka sposobów umożliwiających znalezienie elementu, który ma być badany, za pomocą interfejsu użytkownika aplikacji.

   ::: moniker range=">= vs-2019" 
   **Wybierz element w działającej aplikacji**. Możesz włączyć ten tryb po wybraniu przycisku z lewej strony na pasku narzędzi **aktywnego drzewa wizualnego** . W tym trybie w systemie można wybrać element interfejsu użytkownika w aplikacji, a **dynamiczne drzewo wizualne** (i **przeglądarka właściwości na żywo**) są automatycznie aktualizowane, aby pokazać węzeł w drzewie odpowiadającym temu elementowi i jego właściwości. Począwszy od programu Visual Studio 2019 w wersji 16,4, można [skonfigurować zachowanie wyboru elementu](../debugger/general-debugging-options-dialog-box.md).

   **Wyświetl moduły definiowania układu w działającej aplikacji**. Możesz włączyć ten tryb po wybraniu przycisku bezpośrednio z prawej strony przycisku Włącz wybór. Gdy jest włączona funkcja **modułów definiowania układu wyświetlania** , powoduje, że w oknie aplikacji wyświetlane są poziome i pionowe linie wzdłuż granic zaznaczonego obiektu, dzięki czemu można zobaczyć, jakie elementy są wyrównane do, a także prostokąty pokazujące marginesy. Na przykład Włącz **opcję Wybierz element** i **układ wyświetlania** , a następnie wybierz blok **Dodawanie tekstu elementu** w aplikacji. Powinien zostać wyświetlony węzeł blok tekstu w **dynamicznym drzewie wizualnym** i właściwości bloku tekstu w **podglądzie właściwości na żywo**, a także w poziomie i w pionie na granicach bloku tekstu.

   ![LivePropertyViewer w DisplayLayout](../debugger/media/vs-2019/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer-DisplayLayout")

   **Podgląd zaznaczenia**. Możesz włączyć ten tryb, wybierając trzeci przycisk z lewej strony na dynamicznym pasku narzędzi drzewa wizualnego. Ten tryb pokazuje kod XAML, w którym zadeklarowano element, jeśli masz dostęp do kodu źródłowego aplikacji. Wybierz pozycję **Wybierz element** i **Podgląd zaznaczenia**, a następnie wybierz przycisk w naszej aplikacji testowej. Plik MainWindow. XAML zostanie otwarty w programie Visual Studio, a kursor zostanie umieszczony w wierszu, w którym przycisk jest zdefiniowany.
   ::: moniker-end

   ::: moniker range="vs-2017" 
   **Włącz wybór w działającej aplikacji**. Możesz włączyć ten tryb po wybraniu przycisku z lewej strony na pasku narzędzi **aktywnego drzewa wizualnego** . W tym trybie w systemie można wybrać element interfejsu użytkownika w aplikacji, a **dynamiczne drzewo wizualne** (i **przeglądarka właściwości na żywo**) są automatycznie aktualizowane, aby pokazać węzeł w drzewie odpowiadającym temu elementowi i jego właściwości.

   **Wyświetl moduły definiowania układu w działającej aplikacji**. Możesz włączyć ten tryb po wybraniu przycisku bezpośrednio z prawej strony przycisku Włącz wybór. Gdy jest włączona funkcja **modułów definiowania układu wyświetlania** , powoduje, że w oknie aplikacji wyświetlane są poziome i pionowe linie wzdłuż granic zaznaczonego obiektu, dzięki czemu można zobaczyć, jakie elementy są wyrównane do, a także prostokąty pokazujące marginesy. Na przykład Włącz opcje **Włącz zaznaczenie** i **układ wyświetlania** w, a następnie wybierz blok **Dodawanie tekstu elementu** w aplikacji. Powinien zostać wyświetlony węzeł blok tekstu w **dynamicznym drzewie wizualnym** i właściwości bloku tekstu w **podglądzie właściwości na żywo**, a także w poziomie i w pionie na granicach bloku tekstu.

   ![LivePropertyViewer w DisplayLayout](../debugger/media/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer-DisplayLayout")

   **Podgląd zaznaczenia**. Możesz włączyć ten tryb, wybierając trzeci przycisk z lewej strony na dynamicznym pasku narzędzi drzewa wizualnego. Ten tryb pokazuje kod XAML, w którym zadeklarowano element, jeśli masz dostęp do kodu źródłowego aplikacji. Wybierz pozycję **Włącz zaznaczenie** i **Podgląd zaznaczenia**, a następnie wybierz przycisk w naszej aplikacji testowej. Plik MainWindow. XAML zostanie otwarty w programie Visual Studio, a kursor zostanie umieszczony w wierszu, w którym przycisk jest zdefiniowany.
   ::: moniker-end

## <a name="use-xaml-tools-with-running-applications"></a>Korzystanie z narzędzi XAML z uruchomionymi aplikacjami

Możesz użyć tych narzędzi XAML nawet wtedy, gdy nie masz kodu źródłowego. Po dołączeniu do uruchomionej aplikacji XAML można użyć **drzewa wizualnego na żywo** w elementach interfejsu użytkownika tej aplikacji. Oto przykład użycia tej samej aplikacji testowej WPF, która została wcześniej użyta.

1. Uruchom aplikację **TestXaml** w konfiguracji wydania. Nie można dołączyć do procesu, który jest uruchomiony w konfiguracji **debugowania** .

2. Otwórz drugie wystąpienie programu Visual Studio i kliknij przycisk **debuguj > dołączyć do procesu**. Znajdź **TestXAML. exe** na liście dostępnych procesów, a następnie kliknij przycisk **Dołącz**.

3. Aplikacja zostanie uruchomiona.

4. W drugim wystąpieniu programu Visual Studio Otwórz **dynamiczne drzewo wizualne** (**Debug > Windows > Live Visual Tree**). Powinny być widoczne elementy interfejsu użytkownika **TestXaml** i być możliwe ich manipulowanie tak jak podczas debugowania aplikacji bezpośrednio.

## <a name="see-also"></a>Zobacz też

[Pisanie i debugowanie uruchomionego kodu XAML z gorącą funkcją XAML](xaml-hot-reload.md)
