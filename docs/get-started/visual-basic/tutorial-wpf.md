---
title: Hello world z WPF na Visual Basic
description: Utwórz prostą aplikację .NET dla komputerów z systemem Windows w Visual Basic za Visual Studio przy użyciu Windows Presentation Foundation (WPF).
ms.custom: vs-acquisition, seodec18, get-started
ms.date: 04/23/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
dev_langs:
- VB
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: e757dc25fe094b1ffa745cd43ad251abbc9448a7
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390128"
---
# <a name="tutorial-create-a-simple-application-with-visual-basic"></a>Samouczek: tworzenie prostej aplikacji za pomocą Visual Basic

Ukończenie tego samouczka pozwala zapoznać się z wieloma narzędziami, oknami dialogowymi i projektantami, których można używać podczas tworzenia aplikacji przy użyciu Visual Studio. Utworzysz aplikację "Hello, World", zaprojektujemy interfejs użytkownika, dodamy kod i zdebugujemy błędy, a jednocześnie dowiesz się więcej na temat pracy w zintegrowanym środowisku[projektowym (IDE).](visual-studio-ide.md)

::: moniker range="vs-2017"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [pobierania](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [pobierania](https://visualstudio.microsoft.com/downloads) Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2022"

Jeśli jeszcze nie zainstalowano programu Visual Studio 2022 (wersja zapoznawcza), przejdź do strony pobierania programu [Visual Studio 2022 Preview,](https://visualstudio.microsoft.com/vs/preview/vs2022) aby zainstalować ją bezpłatnie.

::: moniker-end

## <a name="configure-the-ide"></a>Konfigurowanie IDE

::: moniker range="vs-2017"

Po otwarciu Visual Studio po raz pierwszy zostanie wyświetlony monit o zalogowanie. Ten krok jest opcjonalny w tym samouczku. Następnie może zostać wyświetlone okno dialogowe z prośbą o wybranie ustawień programistyki i motywu kolorów. Zachowaj wartości domyślne i wybierz **pozycję Uruchom Visual Studio**.

![Okno dialogowe Wybieranie ustawień](../media/exploreide-settings.png)

Po Visual Studio uruchomieniu zobaczysz okna narzędzi, menu i paski narzędzi oraz obszar okna głównego. Okna narzędzi są zadokowane po lewej i prawej stronie okna aplikacji z **Szybkie uruchamianie,** paskiem menu i standardowym paskiem narzędzi u góry. W środku okna aplikacji znajduje się strona **startowa**. Podczas ładowania rozwiązania lub projektu edytory i projektanci pojawiają się w miejscu, w którym znajduje się **strona startowa.** Podczas tworzenia aplikacji będziesz spędzać większość czasu w tym centralnym obszarze.

![Visual Studio IDE 2017 z zastosowanymi ustawieniami ogólnymi](../media/exploreide-idewithgeneralsettings.png)

::: moniker-end

::: moniker range=">=vs-2019"

Po uruchomieniu Visual Studio zostanie najpierw otwarte okno uruchamiania. Wybierz **pozycję Kontynuuj bez kodu,** aby otworzyć środowisko projektowe. Zobaczysz okna narzędzi, menu i paski narzędzi oraz przestrzeń okna głównego. Okna narzędzi są zadokowane po lewej i prawej stronie okna aplikacji z polem wyszukiwania, paskiem menu i standardowym paskiem narzędzi u góry. Podczas ładowania rozwiązania lub projektu edytory i projektanci są wyświetlane w centralnym miejscu okna aplikacji. Podczas tworzenia aplikacji będziesz spędzać większość czasu w tym centralnym obszarze.

::: moniker-end

## <a name="create-the-project"></a>Tworzenie projektu

Podczas tworzenia aplikacji w programie Visual Studio, należy najpierw utworzyć projekt i rozwiązanie. W tym przykładzie utworzysz projekt Windows Presentation Foundation (WPF).

::: moniker range="vs-2017"

1. Tworzenie nowego projektu. Na pasku menu wybierz pozycję **File** New Project  >  **(Plik nowy**  >  **projekt).**

     ![Na pasku menu wybierz pozycje Plik, Nowy, Projekt](../media/exploreide-filenewproject.png)

2. W **oknie dialogowym Nowy** projekt wybierz Visual Basic Windows Desktop, a następnie wybierz szablon Aplikacja   >    >   **WPF (.NET Framework).** Nadaj **projektowi nazwę HelloWPFApp** i wybierz **przycisk OK.**

     ![Szablon aplikacji WPF w Visual Studio nowy projekt](media/exploreide-newproject-vb.png)

Visual Studio projekt i rozwiązanie HelloWPFApp, a **Eksplorator rozwiązań** wyświetla różne pliki. Projektant **WPF pokazuje** widok projektu i widok XAML *MainWindow.xaml* w widoku podzielonym. Aby wyświetlić więcej lub mniej widoków, można przesunąć podział. Można wybrać wyświetlanie tylko widoku wizualnego lub tylko widoku XAML. Następujące elementy są wyświetlane w **Eksplorator rozwiązań**:

![Eksplorator rozwiązań załadowanych plików HelloWPFApp](../media/exploreide-hellowpfappfiles.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio.

2. Na **ekranie Tworzenie nowego projektu** wyszukaj pozycję "WPF", wybierz pozycję Aplikacja **WPF (.NET Framework),** a następnie wybierz **pozycję Dalej.**

   ![Szablon aplikacji WPF w Visual Studio nowy projekt](media/vs-2019/exploreide-newprojectvb-vs2019.png)

3. Na następnym ekranie nadaj projektowi nazwę **HelloWPFApp** i wybierz **pozycję Utwórz.**

Visual Studio projekt i rozwiązanie HelloWPFApp, a **Eksplorator rozwiązań** wyświetla różne pliki. Projektant **WPF pokazuje** widok projektu i widok XAML *MainWindow.xaml* w widoku podzielonym. Aby wyświetlić więcej lub mniej widoków, można przesunąć podział. Można wybrać wyświetlanie tylko widoku wizualnego lub tylko widoku XAML. Następujące elementy są wyświetlane w **Eksplorator rozwiązań**:

![Eksplorator rozwiązań załadowanych plików HelloWPFApp](../media/vs-2019/exploreide-hellowpfappfiles.png)

::: moniker-end

> [!NOTE]
> Aby uzyskać więcej informacji na temat języka XAML (eXtensible Application Markup Language), zobacz stronę [Omówienie języka XAML dla WPF.](/dotnet/framework/wpf/advanced/xaml-overview-wpf)

Po utworzeniu projektu, można go dostosować. Za pomocą **okna Właściwości** (dostępnego w menu Widok) można wyświetlać i zmieniać opcje elementów projektu, kontrolek i innych elementów w aplikacji. 

### <a name="change-the-name-of-mainwindowxaml"></a>Zmienianie nazwy pliku MainWindow.xaml

Nadajmy bardziej konkretną nazwę mainWindow. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję *MainWindow.xaml* i wybierz polecenie **Zmień nazwę**. Zmień nazwę pliku *na Greetings.xaml.*

## <a name="design-the-user-interface-ui"></a>Zaprojektuj interfejs użytkownika

Jeśli projektant nie jest otwarty, wybierz *pozycję Greetings.xaml* w pliku **Eksplorator rozwiązań**, a następnie naciśnij klawisz  + **F7,** aby otworzyć projektanta.

Dodamy do tej aplikacji trzy typy kontrolek: kontrolkę, dwie kontrolki <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.RadioButton> i <xref:System.Windows.Controls.Button> kontrolkę.

### <a name="add-a-textblock-control"></a>Dodawanie kontrolki TextBlock

1. Naciśnij **klawisze Ctrl** + **Q,** aby aktywować pole wyszukiwania, i wpisz **Toolbox**. Wybierz **pozycję > Przybornik z** listy wyników.

2. W **przyborniku** rozwiń węzeł **Typowe kontrolki WPF,** aby wyświetlić kontrolkę TextBlock.

     ![Przybornik z wyróżniona kontrolką TextBlock](../media/exploreide-textblocktoolbox.png)

3. Dodaj kontrolkę TextBlock do powierzchni projektowej, wybierając element **TextBlock** i przeciągając go do okna na powierzchni projektowej. Wyśrodkuj kontrolkę w górnej części okna. W Visual Studio 2019 r. i nowszych można wyśrodkować kontrolkę przy użyciu czerwonych wytycznych.

Okno powinno wyglądać podobnie, jak na poniższej ilustracji:

![Kontrolka TextBlock w formularzu Greetings](../media/exploreide-greetingswithtextblockonly.png)

Znacznik XAML powinien wyglądać podobnie do poniższego przykładu:

```xaml
<TextBlock HorizontalAlignment="Left" Margin="381,100,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top"/>
```

### <a name="customize-the-text-in-the-text-block"></a>Dostosowywanie tekstu w bloku tekstowym

1. W widoku XAML znajdź znacznik dla elementu TextBlock i zmień atrybut Text:

   ```xaml
   Text="Select a message option and then choose the Display button."
   ```

2. W razie potrzeby ponownie wyśrodkuj element TextBlock i zapisz zmiany, naciskając klawisze Ctrl+S lub używając **elementu** menu Plik.

Następnie dodasz do formularza dwie [kontrolki RadioButton.](/dotnet/framework/wpf/controls/radiobutton)

### <a name="add-radio-buttons"></a>Dodawanie przycisków radiowych

1. W **przyborniku** znajdź **kontrolkę RadioButton.**

     ![Okno przybornika z wybraną kontrolką RadioButton](../media/exploreide-radiobuttontoolbox.png)

2. Dodaj dwie kontrolki RadioButton do powierzchni projektowej, wybierając element **RadioButton** i przeciągając go do okna na powierzchni projektowej. Przenieś przyciski (zaznaczając je i używając klawiszy strzałek), aby przyciski pojawiały się obok kontrolki TextBlock. Użyj czerwonych wytycznych, aby wyrównać kontrolki.

     Okno powinno wyglądać następująco:

     ![Formularz Greetings z kontrolką TextBlock i dwoma przyciskami radiowym](../media/exploreide-greetingswithradiobuttons.png)

3. W **oknie Właściwości** kontrolki RadioButton po lewej stronie zmień właściwość **Name** (właściwość w górnej części **okna Właściwości)** na `HelloButton` .

     ![Okno właściwości RadioButton](../media/exploreide-buttonproperties.png)

4. W **oknie Właściwości** dla prawej kontrolki RadioButton zmień właściwość **Name** na , a następnie `GoodbyeButton` zapisz zmiany.

Możesz teraz dodawać wyświetlany tekst dla każdego formantu RadioButton. Następująca procedura aktualizuje **właściwość Content** kontrolki RadioButton.

### <a name="add-display-text-for-each-radio-button"></a>Dodawanie tekstu wyświetlanego dla każdego przycisku radiowego

Zaktualizuj atrybut **Content** dla `HelloButton` elementów i do i w `GoodbyeButton` `"Hello"` `"Goodbye"` języku XAML. Znacznik XAML powinien teraz wyglądać podobnie do następującego przykładu:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
   </Grid>
   ```

### <a name="set-a-radio-button-to-be-checked-by-default"></a>Ustawianie domyślnego sprawdzenia przycisku radiowego

W tym kroku ustawimy opcję HelloButton tak, aby była domyślnie zaznaczona, tak aby jeden z dwóch przycisków radiowych był zawsze zaznaczony.

W widoku XAML znajdź znacznik HelloButton i dodaj atrybut **IsChecked:**

```xaml
IsChecked="True"
```

Ostatnim elementem interfejsu użytkownika, który dodasz, jest [kontrolka Przycisk.](/dotnet/framework/wpf/controls/button)

### <a name="add-the-button-control"></a>Dodawanie kontrolki przycisku

1. W **przyborniku** znajdź kontrolkę **Przycisk,** a następnie dodaj ją do powierzchni projektowej pod kontrolkami RadioButton, przeciągając ją do formularza w widoku projektu. Jeśli używasz programu Visual Studio 2019 lub nowszego, czerwona linia ułatwia wyśrodkowanie kontrolki.

2. W widoku XAML zmień wartość kontrolki **Content** kontrolki Przycisk z na `Content="Button"` , a następnie zapisz `Content="Display"` zmiany.

     Znacznik powinien przypominać następujący przykład:   `<Button Content="Display" HorizontalAlignment="Left" VerticalAlignment="Top" Width="75" Margin="215,204,0,0"/>`

     Okno powinno wyglądać podobnie, jak na poniższej ilustracji.

     ![Formularz Greetings z etykietami kontrolek](../media/exploreide-greetingswithcontrollabels.png)

### <a name="add-code-to-the-display-button"></a>Dodawanie kodu do przycisku wyświetlania

Gdy ta aplikacja zostanie uruchomiona, po wybraniu przycisku radiowego przez użytkownika zostanie wyświetlone okno komunikatu, a następnie przycisk **Wyświetl.** Jedno okno komunikatu pojawi się, żeby wyświetlić „Hello”, a inne pojawi się, aby wyświetlić „Goodbye”. Aby utworzyć to zachowanie, należy dodać kod do zdarzenia w `Button_Click` *greetings.xaml.vb* lub *Greetings.xaml.cs*.

1. Na powierzchni projektowej kliknij dwukrotnie przycisk **Wyświetl.**

     *Zostanie otwarte okno Greetings.xaml.vb* z kursorem w `Button_Click` zdarzeniu.

    ```vb
    Private Sub Button_Click(sender As Object, e As RoutedEventArgs)

    End Sub
    ```

2. Wprowadź następujący kod:

    ```vb
    If HelloButton.IsChecked = True Then
        MessageBox.Show("Hello.")
    ElseIf GoodbyeButton.IsChecked = True Then
        MessageBox.Show("Goodbye.")
    End If
    ```

3. Zapisz aplikację.

## <a name="debug-and-test-the-application"></a>Debugowanie i testowanie aplikacji

Następnie zdebugujemy aplikację, aby poszukać błędów i sprawdzić, czy oba pola komunikatów są wyświetlane poprawnie. Poniższe instrukcje informują o tym, jak skompilować i uruchomić debuger, ale później możesz zapoznać się z tematami [Build a WPF application (WPF) (Tworzenie aplikacji WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf) i Debug [WPF (Debugowanie WPF),](../../debugger/debugging-wpf.md) aby uzyskać więcej informacji.

### <a name="find-and-fix-errors"></a>Znajdowanie i naprawianie błędów

W tym kroku znajdziesz błąd, który został wcześniej spowodowany przez zmianę nazwy pliku *MainWindow.xaml.*

#### <a name="start-debugging-and-find-the-error"></a>Rozpocznij debugowanie i znajdź błąd

1. Uruchom debuger, naciskając **klawisz F5** lub wybierając pozycję **Debuguj,** a następnie **pozycję Rozpocznij debugowanie.**

   Zostanie **wyświetlone okno Trybu**  przerwania, a okno Dane wyjściowe wskazuje, że wystąpił błąd IOException: Nie można zlokalizować zasobu "mainwindow.xaml".

   ![Zrzut ekranu przedstawiający komunikat IOException](../media/exploreide-ioexception.png)

2. Zatrzymaj debuger, wybierając polecenie  >  **Debuguj zatrzymaj debugowanie.**

Na początku tego samouczka zmieniono nazwę *mainWindow.xaml* na *Greetings.xaml,* ale kod nadal odwołuje się do *pliku MainWindow.xaml* jako do startowego kodu URI aplikacji, więc nie można uruchomić projektu.

#### <a name="specify-greetingsxaml-as-the-startup-uri"></a>Określ greetings.xaml jako startowy URI

1. W **Eksplorator rozwiązań** otwórz plik *Application.xaml.*

2. Zmień `StartupUri="MainWindow.xaml"` na , a następnie zapisz `StartupUri="Greetings.xaml"` zmiany.

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

1. Otwórz *pozycję Greetings.xaml.vb* i wybierz następujący wiersz: `MessageBox.Show(&quot;Hello.")`

2. Dodaj punkt przerwania, naciskając **klawisz F9** lub z menu, wybierając pozycję **Debuguj,** a następnie pozycję Przełącz punkt **przerwania.**

   Obok wiersza kodu na marginesie po lewej stronie okna edytora jest wyświetlane czerwone koło.

3. Wybierz następujący wiersz: `MessageBox.Show("Goodbye.")` .

4. Naciśnij klawisz **F9,** aby dodać punkt przerwania, a następnie naciśnij **klawisz F5,** aby rozpocząć debugowanie.

5. W **oknie Greetings** (Powitania) wybierz przycisk radiowy **Hello (Witaj),** a następnie wybierz **przycisk Display (Wyświetl).**

   Wiersz jest `MessageBox.Show("Hello.")` wyróżniony kolorem żółtym. W dolnej części środowiska IDE okna Automatyczne, Lokalne i Czujka są zadokowane razem po lewej stronie, a okna Stos wywołań, Punkty przerwania, Ustawienia wyjątków, Polecenia, Bezpośrednie i Wyjściowe są zadokowane razem po prawej stronie.

   ![Zrzut ekranu przedstawiający punkt przerwania w debugerze](media/exploreide-debugbreakpoint.png)

6. Na pasku menu wybierz pozycję **Debuguj**  >  **wyetapuj**.

     Aplikacja wznawia wykonywanie i zostanie wyświetlone okno komunikatu ze słowem "Hello".

7. Wybierz przycisk **OK** w oknie komunikatu, aby go zamknąć.

8. W **oknie Greetings** (Powitania) wybierz przycisk radiowy **Wybrań,** a następnie wybierz **przycisk Display (Wyświetl).**

     Wiersz jest `MessageBox.Show("Goodbye.")` wyróżniony kolorem żółtym.

9. Wybierz klawisz **F5,** aby kontynuować debugowanie. Gdy pojawi się okno komunikatu, wybierz przycisk **OK** w oknie komunikatu, aby je zamknąć.

10. Zamknij okno aplikacji, aby zatrzymać debugowanie.

11. Na pasku menu wybierz pozycję **Debuguj**  >  **Wyłącz wszystkie punkty przerwania.**

### <a name="view-a-representation-of-the-ui-elements"></a>Wyświetlanie reprezentacji elementów interfejsu użytkownika

W uruchomionej aplikacji powinien zostać wyświetlony widżet w górnej części okna. Jest to pomocnik środowiska uruchomieniowego, który zapewnia szybki dostęp do niektórych przydatnych funkcji debugowania. Kliknij pierwszy przycisk Go **to Live Visual Tree (Przejdź do drzewa wizualnego na żywo).** Powinno zostać otwarte okno z drzewem zawierającym wszystkie elementy wizualne strony. Rozwiń węzły, aby znaleźć dodane przyciski.

![Zrzut ekranu przedstawiający okno Live Visual Tree (Drzewo wizualne na żywo)](media/vs-2019/exploreide-live-visual-tree.png)

### <a name="build-a-release-version-of-the-application"></a>Tworzenie dystrybucyjnej wersji tej aplikacji

Teraz, po sprawdzeniu, czy wszystko działa, możesz przygotować kompilację wydania aplikacji.

1. W menu głównym wybierz pozycję Build Clean solution **(Kompilowanie** czystego rozwiązania), aby usunąć pliki pośrednie i pliki wyjściowe utworzone  >   podczas poprzednich kompilacji. Nie jest to konieczne, ale czyści dane wyjściowe kompilacji debugowania.

2. Zmień konfigurację kompilacji aplikacji HelloWPFApp z **Debugowanie** na Wydanie, używając kontrolki listy rozwijanej na pasku narzędzi (obecnie wyświetlany jest przycisk "Debuguj"). 

3. Skompilować rozwiązanie, wybierając opcję Build Build Solution   >  **(Skompilowanie rozwiązania kompilacji).**

Gratulujemy ukończenia tego samouczka! Plik, który *został.exe* w katalogu rozwiązania i projektu (*...\HelloWPFApp\HelloWPFApp\bin\Release).*

## <a name="see-also"></a>Zobacz też

::: moniker range="vs-2017"

- [Co nowego w programie Visual Studio 2017](../../ide/whats-new-visual-studio-2017.md)
- [Wskazówki dotyczące produktywności](../../ide/productivity-features.md)

::: moniker-end

::: moniker range="vs-2019"

- [Co nowego w programie Visual Studio 2019](../../ide/whats-new-visual-studio-2019.md)
- [Wskazówki dotyczące produktywności](../../ide/productivity-features.md)

::: moniker-end

::: moniker range="vs-2022"

- [Wskazówki dotyczące produktywności](../../ide/productivity-features.md)

::: moniker-end
