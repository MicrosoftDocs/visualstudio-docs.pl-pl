---
title: Hello world aplikacji za pomocą platformy WPF w programie Visual Basic
description: Utwórz prostą aplikację .NET Desktop dla systemu Windows w Visual Basic z programem Visual Studio przy użyciu platformy interfejsu użytkownika Windows Presentation Foundation (WPF).
ms.custom: seodec18, get-started
ms.date: 04/23/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
dev_langs:
- VB
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 00b8488682674b2531bac561e9f2536e616800fb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944371"
---
# <a name="tutorial-create-a-simple-application-with-visual-basic"></a>Samouczek: tworzenie prostej aplikacji z Visual Basic

Wykonując ten samouczek, zobaczysz wiele narzędzi, okien dialogowych i projektantów, których można używać podczas tworzenia aplikacji w programie Visual Studio. Utworzysz aplikację "Hello, World", projektujesz interfejs użytkownika, dodasz kod i błędy debugowania, podczas gdy uczysz się pracować w zintegrowanym środowisku programistycznym ([IDE](visual-studio-ide.md)).

::: moniker range="vs-2017"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) , aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range=">=vs-2019"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads) , aby zainstalować ją bezpłatnie.

::: moniker-end

## <a name="configure-the-ide"></a>Konfigurowanie IDE

::: moniker range="vs-2017"

Po uruchomieniu programu Visual Studio po raz pierwszy zostanie wyświetlony monit o zalogowanie się. Ten krok jest opcjonalny dla tego samouczka. Następnie może zostać wyświetlone okno dialogowe z prośbą o wybranie ustawień deweloperskich i motywu kolorów. Zachowaj wartości domyślne i wybierz pozycję **Uruchom program Visual Studio**.

![Okno dialogowe Wybieranie ustawień](../media/exploreide-settings.png)

Po uruchomieniu programu Visual Studio zobaczysz okna narzędzi, menu i paski narzędzi oraz przestrzeń okna głównego. Okna narzędzi są zadokowane po lewej i prawej stronie okna aplikacji, z **szybkim uruchamianiem**, paskiem menu i standardowym paskiem narzędzi u góry. Na środku okna aplikacji znajduje się **Strona Start**. Podczas ładowania rozwiązania lub projektu, Edytory i projektanci pojawiają się w miejscu, w którym znajduje się **Strona początkowa** . Podczas opracowywania aplikacji spędzasz najwięcej czasu w tym obszarze centralnym.

![Środowisko IDE programu Visual Studio 2017 z zastosowaniem ustawień ogólnych](../media/exploreide-idewithgeneralsettings.png)

::: moniker-end

::: moniker range=">=vs-2019"

Po uruchomieniu programu Visual Studio, okno uruchamiania zostanie otwarte jako pierwsze. Wybierz pozycję **Kontynuuj bez kodu** , aby otworzyć środowisko programistyczne. Zobaczysz okna narzędzi, menu i paski narzędzi oraz obszar okna głównego. Okna narzędzi są zadokowane po lewej i prawej stronie okna aplikacji, z polem wyszukiwania, paskiem menu i standardowym paskiem narzędzi u góry. Podczas ładowania rozwiązania lub projektu, Edytory i projektanci pojawiają się w centralnym obszarze okna aplikacji. Podczas opracowywania aplikacji spędzasz najwięcej czasu w tym obszarze centralnym.

::: moniker-end

## <a name="create-the-project"></a>Tworzenie projektu

Podczas tworzenia aplikacji w programie Visual Studio, należy najpierw utworzyć projekt i rozwiązanie. Na potrzeby tego przykładu utworzysz projekt Windows Presentation Foundation (WPF).

::: moniker range="vs-2017"

1. Tworzenie nowego projektu. Na pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**.

     ![Na pasku menu wybierz kolejno opcje plik, nowy, projekt.](../media/exploreide-filenewproject.png)

2. W oknie dialogowym **Nowy projekt** wybierz kategorię **zainstalowana**  >  **Visual Basic**  >  **Windows Desktop** , a następnie wybierz szablon **Aplikacja WPF (.NET Framework)** . Nazwij projekt **HelloWPFApp**, a następnie wybierz **przycisk OK**.

     ![Szablon aplikacji WPF w oknie dialogowym Nowy projekt programu Visual Studio](media/exploreide-newproject-vb.png)

Program Visual Studio tworzy projekt i rozwiązanie HelloWPFApp, a **Eksplorator rozwiązań** pokazuje różne pliki. **Projektant WPF** przedstawia widok projektu i widok XAML *MainWindow. XAML* w widoku złożonym. Można przesuwać rozdzielacz, aby pokazać więcej lub mniej jednego widoku. Możesz zobaczyć tylko widok wizualizacji lub tylko widok XAML. Następujące elementy są wyświetlane w **Eksplorator rozwiązań**:

![Eksplorator rozwiązań z załadowanymi plikami HelloWPFApp](../media/exploreide-hellowpfappfiles.png)

::: moniker-end

::: moniker range="vs-2019"

1. Otwórz program Visual Studio 2019.

2. Na ekranie **Tworzenie nowego projektu** Wyszukaj ciąg "WPF" i wybierz pozycję **aplikacja WPF (.NET Framework)**, a następnie wybierz przycisk **dalej**.

   ![Szablon aplikacji WPF w oknie dialogowym Nowy projekt programu Visual Studio](media/vs-2019/exploreide-newprojectvb-vs2019.png)

3. Na następnym ekranie Nadaj projektowi nazwę, **HelloWPFApp** i wybierz pozycję **Utwórz**.

Program Visual Studio tworzy projekt i rozwiązanie HelloWPFApp, a **Eksplorator rozwiązań** pokazuje różne pliki. **Projektant WPF** przedstawia widok projektu i widok XAML *MainWindow. XAML* w widoku złożonym. Można przesuwać rozdzielacz, aby pokazać więcej lub mniej jednego widoku. Możesz zobaczyć tylko widok wizualizacji lub tylko widok XAML. Następujące elementy są wyświetlane w **Eksplorator rozwiązań**:

![Eksplorator rozwiązań z załadowanymi plikami HelloWPFApp](../media/vs-2019/exploreide-hellowpfappfiles.png)

::: moniker-end

> [!NOTE]
> Aby uzyskać więcej informacji na temat języka XAML (eXtensible Application Markup Language), zobacz [Omówienie języka XAML na stronie WPF](/dotnet/framework/wpf/advanced/xaml-overview-wpf) .

Po utworzeniu projektu, można go dostosować. Za pomocą okna **Właściwości** (dostępnego w menu **Widok** ), można wyświetlić i zmienić opcje elementów projektu, formantów i innych elementów w aplikacji.

### <a name="change-the-name-of-mainwindowxaml"></a>Zmień nazwę MainWindow. XAML

Nadaj MainWindow bardziej konkretną nazwę. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję *MainWindow. XAML* i wybierz polecenie **Zmień nazwę**. Zmień nazwę pliku na *Greetings. XAML*.

## <a name="design-the-user-interface-ui"></a>Zaprojektuj interfejs użytkownika

Jeśli projektant nie jest otwarty, wybierz pozycję *Greetings. XAML* w **Eksplorator rozwiązań** i naciśnij klawisz **SHIFT** + **F7** , aby otworzyć projektanta.

Dodamy do tej aplikacji trzy typy kontrolek: <xref:System.Windows.Controls.TextBlock> kontrolka, dwie <xref:System.Windows.Controls.RadioButton> kontrolki i <xref:System.Windows.Controls.Button> kontrolka.

### <a name="add-a-textblock-control"></a>Dodaj kontrolkę TextBlock

1. Naciśnij klawisz **Ctrl** + **Q** , aby uaktywnić pole wyszukiwania i **Przybornik** typów. Wybierz pozycję **wyświetl > przybornika** z listy wyników.

2. W **przyborniku** rozwiń węzeł **formanty wspólnego WPF** , aby zobaczyć formant TextBlock.

     ![Przybornik z wyróżnioną kontrolką TextBlock](../media/exploreide-textblocktoolbox.png)

3. Dodaj kontrolkę TextBlock do powierzchni projektowej, wybierając element **TextBlock** i przeciągając go do okna na powierzchni projektowej. Wyśrodkuj formant w górnej części okna. W programie Visual Studio 2019 lub nowszym można wyśrodkować formant przy użyciu czerwonych wskazówek.

Okno powinno wyglądać podobnie, jak na poniższej ilustracji:

![Kontrolka TextBlock w formularzu Greetings](../media/exploreide-greetingswithtextblockonly.png)

Znacznik XAML powinien wyglądać podobnie do następującego przykładu:

```xaml
<TextBlock HorizontalAlignment="Left" Margin="381,100,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top"/>
```

### <a name="customize-the-text-in-the-text-block"></a>Dostosowywanie tekstu w bloku tekstu

1. W widoku XAML Znajdź znaczniki TextBlock i Zmień atrybut text:

   ```xaml
   Text="Select a message option and then choose the Display button."
   ```

2. W razie potrzeby Wyśrodkuj element TextBlock i Zapisz zmiany, naciskając klawisze CTRL + S lub korzystając z elementu menu **plik** .

Następnie dodasz dwie kontrolki [RadioButton](/dotnet/framework/wpf/controls/radiobutton) do formularza.

### <a name="add-radio-buttons"></a>Dodawanie przycisków radiowych

1. W **przyborniku** Znajdź formant **RadioButton** .

     ![Okno przybornika z wybraną kontrolką RadioButton](../media/exploreide-radiobuttontoolbox.png)

2. Dodaj dwa formanty RadioButton do powierzchni projektowej, wybierając element **RadioButton** i przeciągając go do okna na powierzchni projektowej. Przenieś przyciski (zaznaczając je i używając klawiszy strzałek), aby przyciski pojawiały się obok siebie pod formantem TextBlock. Aby wyrównać kontrolki, użyj czerwonej wskazówki.

     Okno powinno wyglądać następująco:

     ![Formularz Greetings z kontrolką TextBlock i dwoma przyciskami radiowymi](../media/exploreide-greetingswithradiobuttons.png)

3. W oknie **Właściwości** dla lewego formantu RadioButton, Zmień właściwość **name** (właściwość w górnej części okna **Właściwości** ) na `HelloButton` .

     ![Okno właściwości elementu RadioButton](../media/exploreide-buttonproperties.png)

4. W oknie **Właściwości** dla prawego formantu RadioButton, Zmień właściwość **Nazwa** na `GoodbyeButton` , a następnie Zapisz zmiany.

Możesz teraz dodawać wyświetlany tekst dla każdego formantu RadioButton. Poniższa procedura umożliwia zaktualizowanie właściwości **Content** dla kontrolki RadioButton.

### <a name="add-display-text-for-each-radio-button"></a>Dodaj tekst wyświetlany dla każdego przycisku radiowego

Zaktualizuj atrybut **zawartości** dla `HelloButton` i `GoodbyeButton` do `"Hello"` i `"Goodbye"` w języku XAML. Znacznik XAML powinien teraz wyglądać podobnie do poniższego przykładu:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
   </Grid>
   ```

### <a name="set-a-radio-button-to-be-checked-by-default"></a>Ustaw przycisk radiowy do sprawdzenia domyślnego

W tym kroku ustawimy HelloButton do domyślnego sprawdzenia, aby jeden z dwóch przycisków radiowych był zawsze zaznaczony.

W widoku XAML Znajdź znaczniki HelloButton i Dodaj atrybut **IsChecked** :

```xaml
IsChecked="True"
```

Ostatnim elementem interfejsu użytkownika, który dodasz, jest kontrolka [przycisku](/dotnet/framework/wpf/controls/button) .

### <a name="add-the-button-control"></a>Dodaj kontrolkę przycisk

1. W **przyborniku** Znajdź formant **Button** , a następnie dodaj go do powierzchni projektowej pod kontrolkami RadioButton, przeciągając go do formularza w widoku projektu. Jeśli używasz programu Visual Studio 2019 lub nowszego, czerwona linia ułatwia wyśrodkowanie formantu.

2. W widoku XAML Zmień wartość **zawartości** kontrolki Button z `Content="Button"` na `Content="Display"` , a następnie Zapisz zmiany.

     Znacznik powinien wyglądać podobnie do poniższego przykładu:   `<Button Content="Display" HorizontalAlignment="Left" VerticalAlignment="Top" Width="75" Margin="215,204,0,0"/>`

     Okno powinno wyglądać podobnie, jak na poniższej ilustracji.

     ![Formularz pozdrowienia z etykietami kontrolki](../media/exploreide-greetingswithcontrollabels.png)

### <a name="add-code-to-the-display-button"></a>Dodawanie kodu do przycisku wyświetlania

Gdy aplikacja jest uruchomiona, okno komunikatu pojawia się, gdy użytkownik wybierze przycisk radiowy, a następnie wybierze przycisk **wyświetlania** . Jedno okno komunikatu pojawi się, żeby wyświetlić „Hello”, a inne pojawi się, aby wyświetlić „Goodbye”. Aby utworzyć to zachowanie, dodasz kod do `Button_Click` zdarzenia w *Greetings. XAML. vb* lub *Greetings.XAML.cs*.

1. Na powierzchni projektowej kliknij dwukrotnie przycisk **Wyświetl** .

     *Greetings. XAML. vb* zostanie otwarty z kursorem w `Button_Click` zdarzeniu.

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

Następnie debugujesz aplikację, aby wyszukać błędy i przetestować, czy oba okna komunikatów są wyświetlane poprawnie. Poniższe instrukcje przedstawiają sposób kompilowania i uruchamiania debugera, ale w dalszej części można przeczytać [Tworzenie aplikacji WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf) i [debugowania WPF](../../debugger/debugging-wpf.md) , aby uzyskać więcej informacji.

### <a name="find-and-fix-errors"></a>Znajdowanie i naprawianie błędów

W tym kroku znajdziesz błąd, który został wywołany wcześniej przez zmianę nazwy pliku *MainWindow. XAML* .

#### <a name="start-debugging-and-find-the-error"></a>Rozpocznij debugowanie i Znajdź błąd

1. Uruchom Debuger, naciskając klawisz **F5** lub wybierając pozycję **Debuguj**, a następnie **Rozpocznij debugowanie**.

   Zostanie wyświetlone okno **tryb przerwania** , a okno **dane wyjściowe** wskazuje, że wystąpił IOException: nie można zlokalizować zasobu "MainWindow. XAML".

   ![Zrzut ekranu komunikatu IOException](../media/exploreide-ioexception.png)

2. Zatrzymaj debuger, wybierając **Debuguj**  >  **Zatrzymaj debugowanie**.

Zmieniono nazwę *MainWindow. XAML* na *Greetings. XAML* na początku tego samouczka, ale kod nadal odwołuje się do *MainWindow. XAML* jako startowy identyfikator URI dla aplikacji, więc nie można uruchomić projektu.

#### <a name="specify-greetingsxaml-as-the-startup-uri"></a>Określ Greetings. XAML jako startowy identyfikator URI

1. W **Eksplorator rozwiązań** Otwórz plik *Application. XAML* .

2. Zmień `StartupUri="MainWindow.xaml"` na `StartupUri="Greetings.xaml"` , a następnie Zapisz zmiany.

Ponownie uruchom debuger (naciśnij klawisz **F5**). Powinny pojawić się okno **Greetings** aplikacji.

::: moniker range="vs-2017"
![Zrzut ekranu przedstawiający uruchomioną aplikację](media/exploreide-wpf-running-app.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Zrzut ekranu przedstawiający uruchomioną aplikację](media/vs-2019/exploreide-wpf-running-app.png)
::: moniker-end

 Teraz Zamknij okno aplikacji, aby zatrzymać debugowanie.

### <a name="debug-with-breakpoints"></a>Debuguj z punktami przerwania

Możesz przetestować kod podczas debugowania przez dodanie niektórych punktów przerwania. Możesz dodać punkty przerwania, wybierając pozycję **Debuguj**  >  **punkt przerwania**, klikając na lewym marginesie edytora obok wiersza kodu, w którym ma nastąpić przerwanie lub naciskając klawisz **F9**.

#### <a name="add-breakpoints"></a>Dodawanie punktów przerwania

1. Otwórz *Greetings. XAML. vb* i wybierz następujący wiersz: `MessageBox.Show("Hello.")`

2. Dodaj punkt przerwania, naciskając klawisz **F9** lub z menu, wybierając **Debuguj**, a następnie **Przełącz punkt przerwania**.

   Obok wiersza kodu na marginesie po lewej stronie okna edytora jest wyświetlane czerwone koło.

3. Wybierz następujący wiersz: `MessageBox.Show("Goodbye.")` .

4. Naciśnij klawisz **F9** , aby dodać punkt przerwania, a następnie naciśnij klawisz **F5** , aby rozpocząć debugowanie.

5. W oknie **Greetings** wybierz przycisk radiowy **Hello** , a następnie wybierz przycisk **Wyświetl** .

   Wiersz `MessageBox.Show("Hello.")` jest wyróżniony kolorem żółtym. W dolnej części środowiska IDE okna autostarty, lokalne i czujki są zadokowane po lewej stronie, a stos wywołań, punkty przerwania, ustawienia wyjątków, polecenia, natychmiastowe i wyjściowe okna są zadokowane razem po prawej stronie.

   ![Zrzut ekranu punktu przerwania w debugerze](media/exploreide-debugbreakpoint.png)

6. Na pasku menu wybierz polecenie **Debuguj**  >  **krok wychodzący**.

     Aplikacja wznawia wykonywanie i pojawia się okno komunikatu z wyrazem "Hello".

7. Wybierz przycisk **OK** w oknie komunikatu, aby je zamknąć.

8. W oknie **Greetings** wybierz przycisk radiowy **pożegnanie** , a następnie wybierz przycisk **Wyświetl** .

     Wiersz `MessageBox.Show("Goodbye.")` jest wyróżniony kolorem żółtym.

9. Wybierz klawisz **F5** , aby kontynuować debugowanie. Gdy pojawi się okno komunikatu, wybierz przycisk **OK** w oknie komunikatu, aby je zamknąć.

10. Zamknij okno aplikacji, aby zatrzymać debugowanie.

11. Na pasku menu wybierz **Debuguj**  >  **Wyłącz wszystkie punkty przerwania**.

### <a name="view-a-representation-of-the-ui-elements"></a>Wyświetl reprezentację elementów interfejsu użytkownika

W uruchomionej aplikacji powinien zostać wyświetlony widżet pojawiający się w górnej części okna. Jest to pomocnik środowiska uruchomieniowego, który zapewnia szybki dostęp do pewnych przydatnych funkcji debugowania. Kliknij pierwszy przycisk, **Przejdź do dynamicznego drzewa wizualnego**. Powinno zostać wyświetlone okno z drzewem zawierającym wszystkie elementy wizualizacji strony. Rozwiń węzły, aby znaleźć przyciski, które zostały dodane.

![Zrzut ekranu aktywnego okna drzewa wizualnego](media/vs-2019/exploreide-live-visual-tree.png)

### <a name="build-a-release-version-of-the-application"></a>Tworzenie dystrybucyjnej wersji tej aplikacji

Po zweryfikowaniu, że wszystko działa, możesz przygotować kompilację wydania aplikacji.

1. W menu głównym wybierz opcję **Kompiluj**  >  **czyste rozwiązanie** , aby usunąć pliki pośrednie i pliki wyjściowe, które zostały utworzone podczas poprzednich kompilacji. Nie jest to konieczne, ale czyści dane wyjściowe kompilacji debugowania.

2. Zmień konfigurację kompilacji dla HelloWPFApp z **Debug** na **Release** przy użyciu kontrolki menu rozwijanego na pasku narzędzi (jest to komunikat "Debugowanie" jest obecnie).

3. Skompiluj rozwiązanie, wybierając pozycję **Kompiluj**  >  **kompilację rozwiązania**.

Gratulujemy ukończenia tego samouczka. Można znaleźć *plik. exe* , który został utworzony w ramach rozwiązania i katalogu projektu (*. ..\HelloWPFApp\HelloWPFApp\bin\Release*).

## <a name="see-also"></a>Zobacz też

::: moniker range="vs-2017"

- [Co nowego w programie Visual Studio 2017](../../ide/whats-new-visual-studio-2017.md)
- [Wskazówki dotyczące produktywności](../../ide/productivity-features.md)

::: moniker-end

::: moniker range="vs-2019"

- [Co nowego w programie Visual Studio 2019](../../ide/whats-new-visual-studio-2019.md)
- [Wskazówki dotyczące produktywności](../../ide/productivity-features.md)

::: moniker-end