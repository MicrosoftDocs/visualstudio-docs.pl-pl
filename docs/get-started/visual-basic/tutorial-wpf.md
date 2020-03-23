---
title: Aplikacja Hello World z WPF w języku Visual Basic
description: Tworzenie prostej aplikacji Windows Desktop .NET w języku Visual Basic za pomocą programu Visual Studio przy użyciu struktury interfejsu użytkownika programu Windows Presentation Foundation (WPF).
ms.custom: seodec18, get-started
ms.date: 04/23/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: conceptual
dev_langs:
- VB
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d850f709921120fcb85f78f46eb0307d29801d11
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77579952"
---
# <a name="tutorial-create-a-simple-application-with-visual-basic"></a>Samouczek: Tworzenie prostej aplikacji za pomocą języka Visual Basic

Po wykonaniu tego samouczka zapoznasz się z wieloma narzędziami, oknami dialogowymi i projektantami, których można używać podczas tworzenia aplikacji za pomocą programu Visual Studio. Utworzysz aplikację "Hello, World", zaprojektujesz interfejs użytkownika, dodasz kod i błędy debugowania, a jednocześnie dowiesz się o pracy w zintegrowanym środowisku programistycznym[(IDE).](visual-studio-ide.md)

::: moniker range="vs-2017"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range=">=vs-2019"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/downloads) aby zainstalować ją bezpłatnie.

::: moniker-end

## <a name="configure-the-ide"></a>Konfigurowanie IDE

::: moniker range="vs-2017"

Po otwarciu programu Visual Studio po raz pierwszy zostanie wyświetlony monit o zalogowanie się. Ten krok jest opcjonalny dla tego samouczka. Następnie może zostać wyświetlone okno dialogowe z prośbą o wybranie ustawień rozwoju i motywu kolorów. Zachowaj wartości domyślne i wybierz pozycję **Start Visual Studio**.

![Okno dialogowe Wybieranie ustawień](../media/exploreide-settings.png)

Po uruchomieniu programu Visual Studio zobaczysz okna narzędzi, menu i paski narzędzi oraz główne miejsce w oknie. Okna narzędzi są zadokowane po lewej i prawej stronie okna aplikacji, z **szybkim uruchamianiem,** paskiem menu i standardowym paskiem narzędzi u góry. Na środku okna aplikacji znajduje się **strona początkowa**. Po załadowaniu rozwiązania lub projektu edytorzy i projektanci pojawiają się w miejscu, w którym znajduje **się strona początkowa.** Podczas tworzenia aplikacji, będziesz spędzać większość czasu w tym centralnym obszarze.

![Środowisko IDE programu Visual Studio 2017 z zastosowanymi ustawieniami ogólnymi](../media/exploreide-idewithgeneralsettings.png)

::: moniker-end

::: moniker range=">=vs-2019"

Po uruchomieniu programu Visual Studio najpierw zostanie otwarte okno startowe. Wybierz **kontynuuj bez kodu,** aby otworzyć środowisko programistyczne. Zobaczysz okna narzędzi, menu i paski narzędzi oraz główne miejsce w oknie. Okna narzędzi są zadokowane po lewej i prawej stronie okna aplikacji, z polem wyszukiwania, paskiem menu i standardowym paskiem narzędzi u góry. Po załadowaniu rozwiązania lub projektu edytorzy i projektanci pojawiają się w centralnej przestrzeni okna aplikacji. Podczas tworzenia aplikacji, będziesz spędzać większość czasu w tym centralnym obszarze.

::: moniker-end

## <a name="create-the-project"></a>Tworzenie projektu

Podczas tworzenia aplikacji w programie Visual Studio, należy najpierw utworzyć projekt i rozwiązanie. W tym przykładzie utworzysz projekt Fundacji prezentacji systemu Windows (WPF).

::: moniker range="vs-2017"

1. Tworzenie nowego projektu. Na pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**.

     ![Na pasku menu wybierz pozycję Plik, Nowy,](../media/exploreide-filenewproject.png)

2. W oknie dialogowym **Nowy projekt** wybierz kategorię **Zainstalowany** > **pulpit systemu Windows** **Visual Basic,** > a następnie wybierz szablon **Aplikacji WPF (.NET Framework).** Nazwij projekt **HelloWPFApp**i wybierz **przycisk OK**.

     ![Szablon aplikacji WPF w oknie dialogowym Nowy projekt programu Visual Studio](media/exploreide-newproject-vb.png)

Visual Studio tworzy projekt i rozwiązanie HelloWPFApp, a **Eksplorator rozwiązań** pokazuje różne pliki. **Projektant WPF** pokazuje widok projektu i widok XAML *mainwindow.xaml* w widoku podzielonym. Rozdzielacz można przesuwać, aby wyświetlić więcej lub mniej widoku. Można wybrać wyświetlanie tylko widoku wizualnego lub tylko widoku XAML. W **Eksploratorze rozwiązań**pojawiają się następujące elementy:

![Eksplorator rozwiązań z załadowanymi plikami HelloWPFApp](../media/exploreide-hellowpfappfiles.png)

::: moniker-end

::: moniker range="vs-2019"

1. Otwórz program Visual Studio 2019.

2. Na ekranie **Utwórz nowy projekt** wyszukaj hasło "WPF" i wybierz pozycję **WPF App (.NET Framework),** a następnie wybierz pozycję **Dalej**.

   ![Szablon aplikacji WPF w oknie dialogowym Nowy projekt programu Visual Studio](media/vs-2019/exploreide-newprojectvb-vs2019.png)

3. Na następnym ekranie nadaj projektowi nazwę **HelloWPFApp**i wybierz pozycję **Utwórz**.

Visual Studio tworzy projekt i rozwiązanie HelloWPFApp, a **Eksplorator rozwiązań** pokazuje różne pliki. **Projektant WPF** pokazuje widok projektu i widok XAML *mainwindow.xaml* w widoku podzielonym. Rozdzielacz można przesuwać, aby wyświetlić więcej lub mniej widoku. Można wybrać wyświetlanie tylko widoku wizualnego lub tylko widoku XAML. W **Eksploratorze rozwiązań**pojawiają się następujące elementy:

![Eksplorator rozwiązań z załadowanymi plikami HelloWPFApp](../media/vs-2019/exploreide-hellowpfappfiles.png)

::: moniker-end

> [!NOTE]
> Aby uzyskać więcej informacji na temat XAML (eXtensible Application Markup Language), zobacz [omówienie XAML dla WPF](/dotnet/framework/wpf/advanced/xaml-overview-wpf) strony.

Po utworzeniu projektu, można go dostosować. Za pomocą okna **Właściwości** (znajduje się w menu **Widok),** można wyświetlać i zmieniać opcje elementów projektu, formantów i innych elementów w aplikacji.

### <a name="change-the-name-of-mainwindowxaml"></a>Zmienianie nazwy pliku MainWindow.xaml

Nadajmy MainWindow bardziej szczegółową nazwę. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy *plik MainWindow.xaml* i wybierz polecenie **Zmień nazwę**. Zmień nazwę pliku na *Greetings.xaml*.

## <a name="design-the-user-interface-ui"></a>Zaprojektuj interfejs użytkownika

Jeśli projektant nie jest otwarty, wybierz *greetings.xaml* w **Eksploratorze rozwiązań**i naciśnij **klawisz Shift**+**F7,** aby otworzyć projektanta.

Dodamy trzy typy formantów <xref:System.Windows.Controls.TextBlock> do tej <xref:System.Windows.Controls.RadioButton> aplikacji: <xref:System.Windows.Controls.Button> formant, dwa formanty i formant.

### <a name="add-a-textblock-control"></a>Dodawanie kontrolki TextBlock

1. Naciśnij **klawisz Ctrl**+**Q,** aby aktywować pole wyszukiwania i **wpisać przybornik**. Z listy wyników **wybierz pozycję Wyświetl > przyborniku.**

2. W **przyborniku**rozwiń węzeł **Typowe formanty WPF,** aby wyświetlić formant TextBlock.

     ![Przybornik z wyróżnioną kontrolką TextBlock](../media/exploreide-textblocktoolbox.png)

3. Dodaj formant TextBlock do powierzchni projektowej, wybierając element **TextBlock** i przeciągając go do okna na powierzchni projektowej. Wyśrodkuj kontrolka w górnej części okna. W programie Visual Studio 2019 i nowszych można użyć czerwone wskazówki, aby wyśrodkować formant.

Okno powinno wyglądać podobnie, jak na poniższej ilustracji:

![Formant TextBlock w formularzu Pozdrowienia](../media/exploreide-greetingswithtextblockonly.png)

Znaczniki XAML powinny wyglądać mniej więcej tak, jak w poniższym przykładzie:

```xaml
<TextBlock HorizontalAlignment="Left" Margin="381,100,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top"/>
```

### <a name="customize-the-text-in-the-text-block"></a>Dostosowywanie tekstu w bloku tekstu

1. W widoku XAML znajdź znaczniki dla TextBlock i zmień atrybut Tekst:

   ```xaml
   Text="Select a message option and then choose the Display button."
   ```

2. W razie potrzeby ponownie wyśrodkuj blok tekstowy i zapisz zmiany, naciskając klawisze Ctrl+S lub używając elementu menu **Plik.**

Następnie dodasz do formularza dwa formanty [RadioButton.](/dotnet/framework/wpf/controls/radiobutton)

### <a name="add-radio-buttons"></a>Dodawanie przycisków radiowych

1. W **przyborniku**znajdź kontrolkę **RadioButton.**

     ![Okno przybornika z wybraną kontrolką RadioButton](../media/exploreide-radiobuttontoolbox.png)

2. Dodaj dwa formanty RadioButton do powierzchni projektowej, wybierając element **RadioButton** i przeciągając go do okna na powierzchni projektowej. Przenieś przyciski (zaznaczając je i używając klawiszy strzałek), aby przyciski były wyświetlane obok siebie pod kontrolką TextBlock. Użyj czerwonych wskazówek, aby wyrównać formanty.

     Okno powinno wyglądać następująco:

     ![Formularz pozdrowienia z formantem TextBlock i dwoma przyciskami radiowymi](../media/exploreide-greetingswithradiobuttons.png)

3. W oknie **Właściwości** dla lewego formantu RadioButton zmień **właściwość Name (właściwość** `HelloButton`w górnej części okna **Właściwości)** na .

     ![Okno właściwości RadioButton](../media/exploreide-buttonproperties.png)

4. W oknie **Właściwości** dla prawego formantu RadioButton `GoodbyeButton`zmień **właściwość Name** na , a następnie zapisz zmiany.

Możesz teraz dodawać wyświetlany tekst dla każdego formantu RadioButton. Poniższa procedura **aktualizuje Content** właściwości dla kontrolki RadioButton.

### <a name="add-display-text-for-each-radio-button"></a>Dodawanie tekstu wyświetlanego dla każdego przycisku radiowego

Zaktualizuj atrybut `HelloButton` `GoodbyeButton` **Zawartość** `"Goodbye"` dla i do `"Hello"` i w kodzie XAML. Znaczniki XAML powinny teraz wyglądać podobnie do następującego przykładu:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
   </Grid>
   ```

### <a name="set-a-radio-button-to-be-checked-by-default"></a>Ustawianie przycisku opcji do domyślnego sprawdzania

W tym kroku ustawimy HelloButton do sprawdzenia domyślnie, tak aby jeden z dwóch przycisków radiowych był zawsze zaznaczony.

W widoku XAML znajdź znaczniki dla HelloButton i dodaj atrybut **IsChecked:**

```xaml
IsChecked="True"
```

Końcowy element interfejsu użytkownika, który zostanie dodany jest [Button](/dotnet/framework/wpf/controls/button) kontroli.

### <a name="add-the-button-control"></a>Dodawanie kontrolki przycisków

1. W **przyborniku**znajdź kontrolkę **Przycisk,** a następnie dodaj ją do powierzchni projektowej pod kontrolkami RadioButton, przeciągając go do formularza w widoku projektowym. Jeśli używasz programu Visual Studio 2019 lub nowszego, czerwona linia pomaga wyśrodkować formant.

2. W widoku XAML zmień wartość **zawartości** formantu `Content="Button"` `Content="Display"`Przycisk na , a następnie zapisz zmiany.

     Znaczników powinien przypominać następujący przykład:`<Button Content="Display" HorizontalAlignment="Left" VerticalAlignment="Top" Width="75" Margin="215,204,0,0"/>`

     Okno powinno wyglądać podobnie, jak na poniższej ilustracji.

     ![Formularz pozdrowienia z etykietami sterującymi](../media/exploreide-greetingswithcontrollabels.png)

### <a name="add-code-to-the-display-button"></a>Dodaj kod do przycisku wyświetlania

Po uruchomieniu tej aplikacji pojawi się okno komunikatu po wybraniu przez użytkownika przycisku opcji, a następnie wybraniu przycisku **Wyświetl.** Jedno okno komunikatu pojawi się, żeby wyświetlić „Hello”, a inne pojawi się, aby wyświetlić „Goodbye”. Aby utworzyć to zachowanie, dodasz `Button_Click` kod do zdarzenia w *pliku Greetings.xaml.vb* lub *Greetings.xaml.cs*.

1. Na powierzchni projektowej kliknij dwukrotnie przycisk **Wyświetl.**

     *Greetings.xaml.vb* otwiera się z kursorem w wydarzeniu. `Button_Click`

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

Następnie należy debugować aplikację, aby wyszukać błędy i przetestować, czy oba pola komunikatów są wyświetlane poprawnie. Poniższe instrukcje informują, jak skompilować i uruchomić debuger, ale później można przeczytać [Kompilacja aplikacji WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf) i [Debug WPF,](../../debugger/debugging-wpf.md) aby uzyskać więcej informacji.

### <a name="find-and-fix-errors"></a>Znajdowanie i naprawianie błędów

W tym kroku znajdziesz błąd, który spowodował wcześniej, zmieniając nazwę pliku *MainWindow.xaml.*

#### <a name="start-debugging-and-find-the-error"></a>Rozpocznij debugowanie i znajdź błąd

1. Uruchom debuger, naciskając **klawisz F5** lub wybierając **debugowanie**, a następnie **rozpocznij debugowanie**.

   Zostanie wyświetlone okno **Tryb przerwania,** a okno **Dane wyjściowe** wskazuje, że wystąpiło IOException: Nie można zlokalizować zasobu mainwindow.xaml.

   ![Zrzut ekranu przedstawiający komunikat IOException](../media/exploreide-ioexception.png)

2. Zatrzymaj debuger, wybierając **debugowanie** > **zatrzymaj debugowanie**.

Na początku tego samouczka zmieniliśmy nazwę *pliku MainWindow.xaml* na *Greetings.xaml,* ale kod nadal odnosi się do *pliku MainWindow.xaml* jako identyfikator URI uruchamiania aplikacji, więc projekt nie może się uruchomić.

#### <a name="specify-greetingsxaml-as-the-startup-uri"></a>Określanie pliku Greetings.xaml jako identyfikatora URI uruchamiania

1. W **Eksploratorze rozwiązań**otwórz plik *Application.xaml.*

2. Zmień `StartupUri="MainWindow.xaml"` `StartupUri="Greetings.xaml"`na , a następnie zapisz zmiany.

Ponownie uruchom debuger (naciśnij **klawisz F5**). Powinno zostać **wyświetlane** okno Pozdrowienia aplikacji.

::: moniker range="vs-2017"
![Zrzut ekranu przedstawiający uruchamianie aplikacji](media/exploreide-wpf-running-app.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Zrzut ekranu przedstawiający uruchamianie aplikacji](media/vs-2019/exploreide-wpf-running-app.png)
::: moniker-end

 Teraz zamknij okno aplikacji, aby zatrzymać debugowanie.

### <a name="debug-with-breakpoints"></a>Debugowanie z punktami przerwania

Można przetestować kod podczas debugowania, dodając kilka punktów przerwania. Punkty przerwania można dodać, wybierając **pozycję Debug** > **Toggle Breakpoint**, klikając lewy margines edytora obok wiersza kodu, w którym ma wystąpić przerwa, lub naciskając **klawisz F9**.

#### <a name="add-breakpoints"></a>Dodawanie punktów przerwania

1. Otwórz *greetings.xaml.vb*i wybierz następujący wiersz:`MessageBox.Show("Hello.")`

2. Dodaj punkt przerwania, naciskając **klawisz F9** lub z menu, wybierając **debugowanie**, a następnie **przełącz punkt przerwania**.

   Obok wiersza kodu na marginesie po lewej stronie okna edytora jest wyświetlane czerwone koło.

3. Wybierz następujący wiersz: `MessageBox.Show("Goodbye.")`.

4. Naciśnij klawisz **F9,** aby dodać punkt przerwania, a następnie naciśnij **klawisz F5,** aby rozpocząć debugowanie.

5. W oknie **Pozdrowienia** wybierz przycisk opcji **Hello,** a następnie wybierz przycisk **Wyświetl.**

   Linia `MessageBox.Show("Hello.")` jest podświetlona na żółto. U dołu IDE okna Autos, Locals i Watch są zadokowane razem po lewej stronie, a okna Stos wywołań, Punkty przerwania, Ustawienia wyjątków, Polecenie, Natychmiastowe i Wyjściowe są zadokowane razem po prawej stronie.

   ![Zrzut ekranu przedstawiający punkt przerwania w debugerze](media/exploreide-debugbreakpoint.png)

6. Na pasku menu wybierz pozycję **Debug** > **Step Out**.

     Aplikacja wznawia wykonywanie i pojawia się okno komunikatu ze słowem "Hello".

7. Wybierz przycisk **OK** w oknie komunikatu, aby go zamknąć.

8. W oknie **Pozdrowienia** wybierz przycisk opcji **Żegnaj,** a następnie wybierz przycisk **Wyświetl.**

     Linia `MessageBox.Show("Goodbye.")` jest podświetlona na żółto.

9. Wybierz klawisz **F5,** aby kontynuować debugowanie. Po wyświetleniu okna komunikatu wybierz przycisk **OK** w oknie komunikatu, aby go zamknąć.

10. Zamknij okno aplikacji, aby zatrzymać debugowanie.

11. Na pasku menu wybierz pozycję **Debuguj** > **wyłącz wszystkie punkty przerwania**.

### <a name="view-a-representation-of-the-ui-elements"></a>Wyświetlanie reprezentacji elementów interfejsu użytkownika

W uruchomionej aplikacji powinien zostać wyświetlony widżet, który pojawi się w górnej części okna. Jest to pomocnik środowiska uruchomieniowego, który zapewnia szybki dostęp do niektórych przydatnych funkcji debugowania. Kliknij pierwszy przycisk, **Przejdź do żywego drzewa wizualnego**. Powinno zostać wyświetlona okno z drzewem, które zawiera wszystkie elementy wizualne strony. Rozwiń węzły, aby znaleźć dodane przyciski.

![Zrzut ekranu przedstawiający okno Aktywne drzewo wizualne](media/vs-2019/exploreide-live-visual-tree.png)

### <a name="build-a-release-version-of-the-application"></a>Tworzenie dystrybucyjnej wersji tej aplikacji

Teraz, gdy masz zweryfikowane, że wszystko działa, można przygotować kompilację wersji aplikacji.

1. W menu głównym wybierz opcję **Build** > **Clean solution** to delete intermediate files and output files that were created during previous builds. Nie jest to konieczne, ale czyści dane wyjściowe kompilacji debugowania.

2. Zmień konfigurację kompilacji dla HelloWPFApp z **debugowania** do **wydania** przy użyciu formantu rozwijanego na pasku narzędzi (obecnie jest ożywa "Debug").

3. Zbuduj rozwiązanie, wybierając **Build** > **Build Solution**.

Gratulujemy ukończenia tego samouczka! Program *.exe* został utworzony w katalogu rozwiązania i projektu (*...\HelloWPFApp\HelloWPFApp\bin\Release*).

## <a name="see-also"></a>Zobacz też

::: moniker range="vs-2017"

- [Co nowego w programie Visual Studio 2017](../../ide/whats-new-visual-studio-2017.md)
- [Wskazówki dotyczące produktywności](../../ide/productivity-features.md)

::: moniker-end

::: moniker range="vs-2019"

- [Co nowego w programie Visual Studio 2019](../../ide/whats-new-visual-studio-2019.md)
- [Wskazówki dotyczące produktywności](../../ide/productivity-features.md)

::: moniker-end