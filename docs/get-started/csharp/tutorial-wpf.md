---
title: 'Hello world z WPF w języku C #'
description: Tworzenie prostej aplikacji klasycznej .NET systemu Windows w języku C# przy Visual Studio użyciu Windows Presentation Foundation interfejsu użytkownika platformy Windows Presentation Foundation (WPF).
ms.custom: vs-acquisition, get-started
ms.date: 02/10/2021
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: tutorial
dev_langs:
- CSharp
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 268797369fbd878d99028303fa17ba71626a07fb
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390271"
---
# <a name="tutorial-create-a-simple-application-with-c"></a>Samouczek: tworzenie prostej aplikacji w języku C\#

Ukończenie tego samouczka pozwala zapoznać się z wieloma narzędziami, oknami dialogowymi i projektantami, których można używać podczas tworzenia aplikacji przy użyciu Visual Studio. Utworzysz aplikację "Hello, World", zaprojektujemy interfejs użytkownika, dodasz kod i zdebugujemy błędy, a jednocześnie dowiesz się więcej na temat pracy w zintegrowanym środowisku[projektowym (IDE).](visual-studio-ide.md)

## <a name="prerequisites"></a>Wymagania wstępne

::: moniker range="vs-2017"
Jeśli jeszcze nie zainstalowano aplikacji Visual Studio, przejdź [](https://visualstudio.microsoft.com/vs/older-downloads/?) do strony pobierania Visual Studio, aby zainstalować ją bezpłatnie.
::: moniker-end
::: moniker range=">=vs-2019"

- Jeśli jeszcze nie zainstalowano aplikacji Visual Studio, przejdź [](https://visualstudio.microsoft.com/downloads/) do strony pobierania Visual Studio, aby zainstalować ją bezpłatnie.
- W tym samouczku możesz użyć .NET Framework lub .NET Core. .NET Core to nowsza, bardziej nowoczesna framework. Program .NET Core Visual Studio 2019 w wersji 16.3 lub nowszej.
::: moniker-end

## <a name="configure-the-ide"></a>Konfigurowanie IDE

::: moniker range="vs-2017"

Po otwarciu Visual Studio po raz pierwszy zostanie wyświetlony monit o zalogowanie. Ten krok jest opcjonalny w tym samouczku. Następnie może zostać wyświetlone okno dialogowe z prośbą o wybranie ustawień programistycznych i motywu kolorów. Zachowaj wartości domyślne i wybierz pozycję **Uruchom Visual Studio**.

![Okno dialogowe Wybieranie ustawień](../media/exploreide-settings.png)

Po Visual Studio, zobaczysz okna narzędzi, menu i paski narzędzi oraz przestrzeń głównego okna. Okna narzędzi są zadokowane po lewej i prawej stronie okna aplikacji, a Szybkie uruchamianie **,** pasek menu i standardowy pasek narzędzi u góry. W środku okna aplikacji znajduje się strona **startowa**. Podczas ładowania rozwiązania lub projektu edytory i projektanci są wyświetlane w miejscu, w którym znajduje się **strona** startowa. Podczas opracowywania aplikacji będziesz spędzać większość czasu w tym centralnym obszarze.

![Visual Studio 2017 IDE z zastosowanymi ustawieniami ogólnymi](../media/exploreide-idewithgeneralsettings.png "Zrzut ekranu przedstawiający Visual Studio IDE programu 2017 z zastosowanymi ustawieniami ogólnymi")

::: moniker-end

::: moniker range=">=vs-2019"

Po uruchomieniu Visual Studio najpierw zostanie otwarte okno uruchamiania. Wybierz **pozycję Kontynuuj bez kodu,** aby otworzyć środowisko projektowe. Zobaczysz okna narzędzi, menu i paski narzędzi oraz przestrzeń głównego okna. Okna narzędzi są zadokowane po lewej i prawej stronie okna aplikacji z polem wyszukiwania, paskiem menu i standardowym paskiem narzędzi u góry. Podczas ładowania rozwiązania lub projektu edytory i projektanci są wyświetlane w centralnym miejscu okna aplikacji. Podczas opracowywania aplikacji będziesz spędzać większość czasu w tym centralnym obszarze.

::: moniker-end

## <a name="create-the-project"></a>Tworzenie projektu

Podczas tworzenia aplikacji w programie Visual Studio, należy najpierw utworzyć projekt i rozwiązanie. W tym przykładzie utworzysz projekt Windows Presentation Foundation (WPF).

::: moniker range="vs-2017"

1. Tworzenie nowego projektu. Na pasku menu wybierz pozycję **File** New Project  >  **(Plik nowego**  >  **projektu).**

     ![Na pasku menu wybierz pozycję Plik, Nowy, Projekt](../media/exploreide-filenewproject.png "Zrzut ekranu przedstawiający pasek menu, na którym wybierasz pozycje Plik, Nowy, Projekt")

1. W **oknie dialogowym Nowy** projekt wybierz kategorię **Zainstalowany** program Visual C# dla programu Windows Desktop, a następnie wybierz szablon  >    >   **Aplikacja WPF (.NET Framework).** Nadaj **projektowi nazwę HelloWPFApp** i wybierz **przycisk OK.**

     ![Szablon aplikacji WPF w Visual Studio nowy projekt](media/exploreide-newprojectcsharp.png "Zrzut ekranu przedstawiający szablon aplikacji WPF w oknie dialogowym Nowy projekt")

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio.

1. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt.**

   ![Wyświetlanie okna "Tworzenie nowego projektu"](../../get-started/media/vs-2019/start-window-create-new-project.png "Zrzut ekranu przedstawiający okno &quot;Tworzenie nowego projektu&quot;")

1. Na **ekranie Tworzenie nowego projektu** wyszukaj pozycję "WPF", wybierz pozycję **Aplikacja WPF,** a następnie wybierz pozycję **Dalej.**

   :::image type="content" source="media/vs-2019/explore-ide-new-project-csharp-vs-2019.png" alt-text="Szablon aplikacji WPF w oknie dialogowym &quot;Tworzenie nowego projektu&quot;":::

1. Na następnym ekranie nadaj projektowi nazwę **HelloWPFApp** i wybierz pozycję **Dalej.**

   :::image type="content" source="./media/vs-2019/explore-ide-name-project.png" alt-text="Nadaj projektowi nazwę &quot;HelloWPFApp&quot;":::

1. W **oknie Dodatkowe informacje** dla struktury docelowej należy już wybrać platformę **.NET Core 3.1.** Jeśli nie, wybierz **pozycję .NET Core 3.1.** Następnie wybierz pozycję **Utwórz.**

   :::image type="content" source="./media/vs-2019/wpf-target-framework.png" alt-text="W oknie &quot;Dodatkowe informacje&quot; upewnij się, że wybrano opcję .NET Core 3.1":::

::: moniker-end

Visual Studio tworzy projekt i rozwiązanie HelloWPFApp, a **Eksplorator rozwiązań** wyświetla różne pliki. Projektant **WPF pokazuje** widok projektu i widok XAML *pliku MainWindow.xaml* w widoku podzielonym. Aby wyświetlić więcej lub mniej widoków, można przesuwać suwak. Możesz wybrać wyświetlanie tylko widoku wizualnego lub tylko widoku XAML.

![Projekt i rozwiązanie WPF w ide](media/exploreide-wpfproject-cs.png "Zrzut ekranu przedstawiający projekt i rozwiązanie WPF w ide")

> [!NOTE]
> Aby uzyskać więcej informacji na temat języka XAML (eXtensible Application Markup Language), zobacz [stronę Omówienie języka XAML dla platformy WPF.](/dotnet/framework/wpf/advanced/xaml-overview-wpf)

Po utworzeniu projektu, można go dostosować. W tym celu wybierz pozycję **Okno właściwości** z menu **Widok** lub naciśnij **klawisz F4.** Następnie można wyświetlać i zmieniać opcje elementów projektu, kontrolek i innych elementów w aplikacji.

   ![Okno właściwości](../media/exploreide-hellowpfappfiles.png "Zrzut ekranu przedstawiający okno Właściwości z nazwami aplikacji plików WPF")   

### <a name="change-the-name-of-mainwindowxaml"></a>Zmienianie nazwy pliku MainWindow.xaml

Nadajmy nazwę MainWindow bardziej konkretną. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję *MainWindow.xaml* i wybierz polecenie **Zmień nazwę**. Zmień nazwę pliku na *Greetings.xaml.*

## <a name="design-the-user-interface-ui"></a>Zaprojektuj interfejs użytkownika

Jeśli projektant nie jest otwarty, wybierz *pozycję Greetings.xaml* i naciśnij klawisz  + **Shift F7,** aby otworzyć projektanta.

Dodamy do tej aplikacji trzy typy kontrolek: kontrolkę, dwie kontrolki <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.RadioButton> i <xref:System.Windows.Controls.Button> kontrolkę.

### <a name="add-a-textblock-control"></a>Dodawanie kontrolki TextBlock

1. Naciśnij **klawisze Ctrl** + **Q,** aby aktywować pole wyszukiwania, i wpisz **Przybornik**. Wybierz **pozycję > przybornik z** listy wyników.

1. W **przyborniku** rozwiń węzeł **Typowe kontrolki WPF,** aby wyświetlić kontrolkę TextBlock.

     ![Przybornik z wyróżniona kontrolką TextBlock](../media/exploreide-textblocktoolbox.png "Zrzut ekranu przedstawiający okno przybornika z wyróżniona kontrolką TextBlock")

1. Dodaj kontrolkę TextBlock do powierzchni projektowej, wybierając element **TextBlock** i przeciągając go do okna na powierzchni projektowej. Wyśrodkowanie kontrolki w górnej części okna. W Visual Studio 2019 r. i nowszych można wyśrodkować kontrolkę przy użyciu czerwonych wytycznych.

    Okno powinno wyglądać podobnie, jak na poniższej ilustracji:

    ![Kontrolka TextBlock w formularzu Greetings](../media/exploreide-greetingswithtextblockonly.png "Zrzut ekranu przedstawiający kontrolkę TextBlock w formularzu Greetings")

   Znacznik XAML powinien wyglądać podobnie do poniższego przykładu:

    ```xaml
    <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="387,60,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top"/>
    </Grid>
    ```

### <a name="customize-the-text-in-the-text-block"></a>Dostosowywanie tekstu w bloku tekstowym

1. W widoku XAML znajdź znacznik dla elementu **TextBlock** i zmień atrybut **Text** z `TextBox` na `Select a message option and then choose the Display button.`

   Znacznik XAML powinien wyglądać podobnie do poniższego przykładu:

   ```xaml
   <Grid>
       <TextBlock HorizontalAlignment="Left" Margin="387,60,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
   </Grid>
   ```

1. Jeśli chcesz, wyśrodkuj ponownie element TextBlock, a następnie zapisz zmiany, naciskając klawisze **Ctrl+S** lub używając **elementu** menu Plik.

Następnie dodasz dwie [kontrolki RadioButton](/dotnet/framework/wpf/controls/radiobutton) do formularza.

### <a name="add-radio-buttons"></a>Dodawanie przycisków radiowych

1. W **przyborniku** znajdź **kontrolkę RadioButton.**

     ![Okno przybornika z wybraną kontrolką RadioButton](../media/exploreide-radiobuttontoolbox.png "Zrzut ekranu przedstawiający okno przybornika z wybraną kontrolką RadioButton")

1. Dodaj dwie kontrolki RadioButton do powierzchni projektowej, wybierając element **RadioButton** i przeciągając go do okna na powierzchni projektowej. Przenieś przyciski (zaznaczając je i używając klawiszy strzałek), aby przyciski pojawiały się obok kontrolki TextBlock. Użyj czerwonych wytycznych, aby wyrównać kontrolki.

   Okno powinno wyglądać następująco:

   ![Formularz Powitanie z tekstem TextBlock i dwoma przyciskami radiowym](../media/exploreide-greetingswithradiobuttons.png "Zrzut ekranu przedstawiający formularz Greetings z tekstem TextBlock i dwoma przyciskami radiowym")

1. W **oknie Właściwości** lewej kontrolki RadioButton zmień właściwość **Name** (właściwość w górnej części okna **Właściwości)** na `HelloButton` .

    ![Okno właściwości RadioButton](../media/exploreide-buttonproperties.png "Zrzut ekranu przedstawiający okno właściwości przycisku RadioButton")

1. W **oknie Właściwości** dla prawej kontrolki RadioButton zmień właściwość **Name** na , a następnie `GoodbyeButton` zapisz zmiany.

Następnie dodasz tekst wyświetlany dla każdej kontrolki RadioButton. Następująca procedura aktualizuje **właściwość Content** kontrolki RadioButton.

### <a name="add-display-text-for-each-radio-button"></a>Dodawanie tekstu wyświetlanego dla każdego przycisku radiowego

1. Zaktualizuj atrybut **Content** dla elementów `HelloButton` i do i w `GoodbyeButton` `"Hello"` `"Goodbye"` języku XAML. Znacznik XAML powinien teraz wyglądać podobnie do poniższego przykładu:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
   </Grid>
   ```

### <a name="set-a-radio-button-to-be-checked-by-default"></a>Ustawianie domyślnego sprawdzenia przycisku radiowego

W tym kroku ustawimy opcję HelloButton tak, aby była domyślnie zaznaczona, aby zawsze był wybrany jeden z dwóch przycisków radiowych.

1. W widoku XAML znajdź znacznik HelloButton.

1. Dodaj atrybut **IsChecked** i ustaw go na **wartość True.** W szczególności `IsChecked="True"` dodaj .

   Znacznik XAML powinien teraz wyglądać podobnie do poniższego przykładu:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" IsChecked="True" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
   </Grid>
   ```

Ostatnim elementem interfejsu użytkownika, który dodasz, jest [kontrolka](/dotnet/framework/wpf/controls/button) Przycisk.

### <a name="add-the-button-control"></a>Dodawanie kontrolki przycisku

1. W **przyborniku** znajdź kontrolkę **Przycisk,** a następnie dodaj ją do powierzchni projektowej pod kontrolkami RadioButton, przeciągając ją do formularza w widoku projektu. Jeśli używasz programu Visual Studio 2019 lub nowszego, czerwona linia ułatwia wyśrodkowanie kontrolki.

1. W widoku XAML zmień wartość kontrolki **Content** dla kontrolki Przycisk z na `Content="Button"` , a następnie zapisz `Content="Display"` zmiany.

     Okno powinno wyglądać podobnie, jak na poniższej ilustracji.

     ![Formularz Greetings z etykietami kontrolek](media/exploreide-greetingswithcontrollabels-cs.png "Zrzut ekranu przedstawiający formularz Greetings z etykietami kontrolek")

   Znacznik XAML powinien teraz wyglądać podobnie do poniższego przykładu:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" IsChecked="True" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
        <Button Content="Display" HorizontalAlignment="Left" Margin="377,270,0,0" VerticalAlignment="Top" Width="75"/>
   </Grid>
   ```

### <a name="add-code-to-the-display-button"></a>Dodawanie kodu do przycisku wyświetlania

Gdy ta aplikacja zostanie uruchomiona, po wybraniu przycisku radiowego przez użytkownika zostanie wyświetlone okno komunikatu, a następnie przycisk **Wyświetl.** Jedno okno komunikatu pojawi się, żeby wyświetlić „Hello”, a inne pojawi się, aby wyświetlić „Goodbye”. Aby utworzyć to zachowanie, dodasz kod do zdarzenia `Button_Click` w *pliku Greetings.xaml.cs*.

1. Na powierzchni projektowej kliknij dwukrotnie przycisk **Wyświetl.**

     *Zostanie otwarty plik Greetings.xaml.cs* z kursorem w `Button_Click` zdarzeniu.

    ```csharp
    private void Button_Click(object sender, RoutedEventArgs e)
    {

    }
    ```

1. Wprowadź następujący kod:

    ```csharp
    if (HelloButton.IsChecked == true)
    {
         MessageBox.Show("Hello.");
    }
    else if (GoodbyeButton.IsChecked == true)
    {
        MessageBox.Show("Goodbye.");
    }
    ```

1. Zapisz aplikację.

## <a name="debug-and-test-the-application"></a>Debugowanie i testowanie aplikacji

Następnie zdebugujemy aplikację, aby poszukać błędów i sprawdzić, czy oba pola komunikatów są wyświetlane poprawnie. Poniższe instrukcje informują o tym, jak skompilować i uruchomić debuger, ale później możesz zapoznać się z tematami [Build a WPF application (WPF) (Tworzenie aplikacji WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf) i Debug [WPF (Debugowanie WPF),](../../debugger/debugging-wpf.md) aby uzyskać więcej informacji.

### <a name="find-and-fix-errors"></a>Znajdowanie i naprawianie błędów

W tym kroku znajdziesz błąd, który został wcześniej spowodowany przez zmianę nazwy pliku *MainWindow.xaml.*

#### <a name="start-debugging-and-find-the-error"></a>Rozpocznij debugowanie i znajdź błąd

1. Uruchom debuger, naciskając **klawisz F5** lub wybierając pozycję **Debuguj,** a następnie **pozycję Rozpocznij debugowanie.**

   Zostanie **wyświetlone okno Trybu**  przerwania, a okno Dane wyjściowe wskazuje, że wystąpił błąd IOException: Nie można zlokalizować zasobu "mainwindow.xaml".

   ![Komunikat IOException](../media/exploreide-ioexception.png "Zrzut ekranu przedstawiający komunikat IOException")

1. Zatrzymaj debuger, wybierając polecenie  >  **Debuguj zatrzymaj debugowanie.**

Na początku tego samouczka zmieniono nazwę *mainWindow.xaml* na *Greetings.xaml,* ale kod nadal odwołuje się do *pliku MainWindow.xaml* jako do startowego kodu URI aplikacji, więc nie można uruchomić projektu.

#### <a name="specify-greetingsxaml-as-the-startup-uri"></a>Określ greetings.xaml jako startowy URI

1. W **Eksplorator rozwiązań** otwórz plik *App.xaml.*

1. Zmień `StartupUri="MainWindow.xaml"` na , a następnie zapisz `StartupUri="Greetings.xaml"` zmiany.

Uruchom debuger ponownie (naciśnij **klawisz F5).** Powinno zostać otwarte **okno Powitanie** aplikacji.

::: moniker range="vs-2017"
![Zrzut ekranu przedstawiający uruchamianie aplikacji](media/exploreide-wpf-running-app.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Zrzut ekranu przedstawiający uruchamianie aplikacji](media/vs-2019/exploreide-wpf-running-app.png)
::: moniker-end

Teraz zamknij okno aplikacji, aby zatrzymać debugowanie.

### <a name="debug-with-breakpoints&quot;></a>Debugowanie za pomocą punktów przerwania

Kod można przetestować podczas debugowania, dodając kilka punktów przerwania. Punkty przerwania można dodać, wybierając pozycję Debuguj Przełącz punkt przerwania, klikając lewy margines edytora obok wiersza kodu, w którym ma wystąpić przerwa, lub naciskając  >   **klawisz F9**.

#### <a name=&quot;add-breakpoints&quot;></a>Dodawanie punktów przerwania

1. Otwórz *pozycję Greetings.xaml.cs* i wybierz następujący wiersz: `MessageBox.Show(&quot;Hello.")`

1. Dodaj punkt przerwania z menu, wybierając pozycję **Debuguj,** a **następnie pozycję Przełącz punkt przerwania.**

     Obok wiersza kodu na marginesie po lewej stronie okna edytora jest wyświetlane czerwone koło.

1. Wybierz następujący wiersz: `MessageBox.Show("Goodbye.")` .

1. Naciśnij klawisz **F9,** aby dodać punkt przerwania, a następnie naciśnij **klawisz F5,** aby rozpocząć debugowanie.

1. W **oknie Greetings** (Powitania) wybierz przycisk radiowy **Hello (Witaj),** a następnie wybierz **przycisk Display (Wyświetl).**

    Wiersz jest `MessageBox.Show("Hello.")` wyróżniony kolorem żółtym. W dolnej części środowiska IDE okna Automatyczne, Lokalne i Czujka są zadokowane razem po lewej stronie, a okna Stos wywołań, Punkty przerwania, Ustawienia wyjątków, Polecenia, Bezpośrednie i Wyjściowe są zadokowane razem po prawej stronie.

    ![Punkt przerwania w debugerze](media/exploreide-debugbreakpoint.png "Zrzut ekranu przedstawiający punkt przerwania w debugerze")

1. Na pasku menu wybierz pozycję **Debuguj**  >  **wyetapuj**.

     Aplikacja wznawia wykonywanie i zostanie wyświetlone okno komunikatu ze słowem "Hello".

1. Wybierz przycisk **OK** w oknie komunikatu, aby go zamknąć.

1. W **oknie Greetings** (Powitania) wybierz przycisk radiowy **Wybrań,** a następnie wybierz **przycisk Display (Wyświetl).**

     Wiersz jest `MessageBox.Show("Goodbye.")` wyróżniony kolorem żółtym.

1. Wybierz klawisz **F5,** aby kontynuować debugowanie. Gdy pojawi się okno komunikatu, wybierz przycisk **OK** w oknie komunikatu, aby je zamknąć.

1. Zamknij okno aplikacji, aby zatrzymać debugowanie.

1. Na pasku menu wybierz pozycję **Debuguj**  >  **Wyłącz wszystkie punkty przerwania.**

### <a name="view-a-representation-of-the-ui-elements"></a>Wyświetlanie reprezentacji elementów interfejsu użytkownika

W uruchomionej aplikacji powinien zostać wyświetlony widżet w górnej części okna. Jest to pomocnik środowiska uruchomieniowego, który zapewnia szybki dostęp do niektórych przydatnych funkcji debugowania. Kliknij pierwszy przycisk Go **to Live Visual Tree (Przejdź do drzewa wizualnego na żywo).** Powinno zostać otwarte okno z drzewem zawierającym wszystkie elementy wizualne strony. Rozwiń węzły, aby znaleźć dodane przyciski.

![Zrzut ekranu przedstawiający okno Live Visual Tree (Drzewo wizualne na żywo)](media/vs-2019/exploreide-live-visual-tree.png)

### <a name="build-a-release-version-of-the-application"></a>Tworzenie dystrybucyjnej wersji tej aplikacji

Teraz, po sprawdzeniu, czy wszystko działa, możesz przygotować kompilację wydania aplikacji.

1. W menu głównym wybierz pozycję Build Clean solution **(Kompilowanie** czystego rozwiązania), aby usunąć pliki pośrednie i pliki wyjściowe utworzone  >   podczas poprzednich kompilacji. Nie jest to konieczne, ale czyści dane wyjściowe kompilacji debugowania.

1. Zmień konfigurację kompilacji aplikacji HelloWPFApp z **Debugowanie** na Wydanie, używając kontrolki listy rozwijanej na pasku narzędzi (obecnie wyświetlany jest przycisk "Debuguj"). 

1. Skompilować rozwiązanie, wybierając opcję Build Build Solution   >  **(Skompilowanie rozwiązania kompilacji).**

Gratulujemy ukończenia tego samouczka! Plik, który *został.exe* w katalogu rozwiązania i projektu (*...\HelloWPFApp\HelloWPFApp\bin\Release).*

## <a name="next-steps"></a>Następne kroki

Gratulujemy ukończenia tego samouczka! Aby dowiedzieć się więcej, przejdź do następujących samouczków.

> [!div class="nextstepaction"]
> [Kontynuuj pracę z większej liczby samouczków platformy WPF](/dotnet/framework/wpf/getting-started/wpf-walkthroughs/)

## <a name="see-also"></a>Zobacz też

- [Wskazówki dotyczące produktywności](../../ide/productivity-features.md)
