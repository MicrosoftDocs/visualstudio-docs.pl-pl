---
title: 'Samouczek: Aplikacja Hello World z Windows Presentation Foundation (WPF) wC#'
description: Utwórz prostą aplikację Windows Desktop .NET w C# z programem Visual Studio przy użyciu struktury interfejsu użytkownika Windows Presentation Foundation (WPF).
ms.custom: seodec18, get-started
ms.date: 03/28/2019
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
dev_langs:
- CSharp
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ad5112313b57f4757c86a202cfdc711e9b478e1e
ms.sourcegitcommit: b14b7a938a2aba9fcce4d5e813aadf2040b0dcda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/29/2019
ms.locfileid: "58647521"
---
# <a name="tutorial-create-a-simple-application-with-c"></a>Samouczek: Tworzenie prostej aplikacji przy użyciu języka C\#

Przez wykonanie kroków tego samouczka, zapoznasz się z wieloma narzędziami, okna dialogowe i projektantach, które można użyć podczas tworzenia aplikacji za pomocą programu Visual Studio. Będzie utworzyć aplikację "Hello, World", zaprojektujesz interfejs użytkownika, należy dodać kod i zdebugujesz błędy, podczas gdy Dowiedz się więcej o pracy w zintegrowanym środowisku programistycznym ([IDE](visual-studio-ide.md)).

::: moniker range="vs-2017"
Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) strony, aby zainstalować go za darmo.
::: moniker-end
::: moniker range=">=vs-2019"
Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019+rc) strony, aby zainstalować go za darmo.
::: moniker-end

## <a name="configure-the-ide"></a>Konfigurowanie IDE

::: moniker range="vs-2017"

Po otwarciu programu Visual Studio po raz pierwszy, zostanie wyświetlony monit do logowania. Ten krok jest opcjonalny w tym samouczku. Następnie możesz mogą być wyświetlane okno dialogowe z prośbą o wybierz ustawienia środowiska deweloperskiego i motyw kolorów. Pozostaw wartości domyślne, a następnie wybierz **Uruchom program Visual Studio**.

![Wybierz ustawienia, okno dialogowe](../media/exploreide-settings.png)

Po uruchomieniu programu Visual Studio, zostaną wyświetlone okna narzędzi, menu i paski narzędzi oraz przestrzeń głównego okna. Okna narzędzi są zadokowane po lewej i prawej stronie okna aplikacji za pomocą **Szybkie uruchamianie**, pasek menu i standardowy pasek narzędzi u góry. Na środku okna aplikacji znajduje **strona startowa**. Podczas ładowania rozwiązania lub projektu, edytory i projektanty są wyświetlane w miejscu gdzie **strona startowa** jest. Podczas opracowywania aplikacji spędzisz większość czasu w tym środkowym obszarze.

![Visual Studio 2017 IDE z zastosowaniem ustawień ogólnych](../media/exploreide-idewithgeneralsettings.png)

::: moniker-end

::: moniker range=">=vs-2019"

Po uruchomieniu programu Visual Studio, najpierw zostanie otwarte okno rozpoczęcia. Wybierz **Kontynuuj bez konieczności pisania kodu** otworzyć środowisko programistyczne. Zobaczysz okien narzędzi, menu i paski narzędzi oraz przestrzeń głównego okna. Okna narzędziowe są zadokowane po lewej i prawej stronie okna aplikacji przy użyciu pola wyszukiwania, na pasku menu i standardowy pasek narzędzi u góry. Podczas ładowania rozwiązania lub projektu, edytory i projektanty są wyświetlane w centralne miejsce w oknie aplikacji. Podczas opracowywania aplikacji spędzisz większość czasu w tym środkowym obszarze.

::: moniker-end

## <a name="create-the-project"></a>Utwórz projekt

Podczas tworzenia aplikacji w programie Visual Studio, należy najpierw utworzyć projekt i rozwiązanie. W tym przykładzie utworzysz projekt Windows Presentation Foundation (WPF).

::: moniker range="vs-2017"

1. Utwórz nowy projekt. Na pasku menu wybierz **pliku** > **New** > **projektu**.

     ![Na pasku menu wybierz plik, nowy projekt](../media/exploreide-filenewproject.png)

1. W **nowy projekt** okno dialogowe, wybierz opcję **zainstalowane** > **Visual C#**   >  **Windows Desktop**kategorii, a następnie wybierz **aplikacja WPF (.NET Framework)** szablonu. Nadaj projektowi nazwę **HelloWPFApp**i wybierz **OK**.

     ![Szablon aplikacji WPF w oknie dialogowym Nowy projekt programu Visual Studio](media/exploreide-newprojectcsharp.png)

Program Visual Studio tworzy projekt i rozwiązanie HelloWPFApp, i **Eksploratora rozwiązań** pokazuje różne pliki. **WPF Designer** Pokazuje widok projektu i widok XAML *MainWindow.xaml* w widoku podzielonym. Przesuń, rozdzielacza, aby wyświetlić więcej lub mniej albo widoku. Można wyświetlić tylko visual widoku lub w widoku XAML. Następujące elementy są wyświetlane w **Eksploratora rozwiązań**:

![Eksplorator rozwiązań z plikami HelloWPFApp załadowany](../media/exploreide-hellowpfappfiles.png)

> [!NOTE]
> Aby uzyskać więcej informacji na temat XAML (eXtensible Application Markup Language), zobacz [Przegląd XAML dla WPF](/dotnet/framework/wpf/advanced/xaml-overview-wpf) strony.

Po utworzeniu projektu, można go dostosować. Za pomocą **właściwości** okna (znalezione na **widoku** menu), można wyświetlić i zmienić opcje elementów projektu, formantów i innych elementów w aplikacji.

::: moniker-end

::: moniker range="vs-2019"

1. Open Visual Studio 2019.

1. W oknie rozpoczęcia wybierz **Tworzenie nowego projektu**. 

   ![Wyświetlanie w oknie "Tworzenie nowego projektu"](../../get-started/media/vs-2019/start-window-create-new-project.png)


2. Na **Utwórz nowy projekt** ekran, wyszukaj "WPF", wybierz **aplikacja WPF (.NET Framework)**, a następnie wybierz **dalej**.

   ![Szablon aplikacji WPF w oknie dialogowym z "Tworzenie nowego projektu"](media/vs-2019/exploreide-newprojectcsharp-vs2019.png)

3. Na następnym ekranie, nazwij projekt, **HelloWPFApp**i wybierz polecenie **Utwórz**.

   ![w oknie "Konfigurowanie nowego projektu" nazwij swój projekt "HelloWPFApp"](./media/vs-2019/exploreide-nameproject.png)
 
Program Visual Studio tworzy projekt i rozwiązanie HelloWPFApp, i **Eksploratora rozwiązań** pokazuje różne pliki. **WPF Designer** Pokazuje widok projektu i widok XAML *MainWindow.xaml* w widoku podzielonym. Przesuń, rozdzielacza, aby wyświetlić więcej lub mniej albo widoku. Można wyświetlić tylko visual widoku lub w widoku XAML. Następujące elementy są wyświetlane w **Eksploratora rozwiązań**:

![Eksplorator rozwiązań z plikami HelloWPFApp załadowany](../media/vs-2019/exploreide-hellowpfappfiles.png)

> [!NOTE]
> Aby uzyskać więcej informacji na temat XAML (eXtensible Application Markup Language), zobacz [Przegląd XAML dla WPF](/dotnet/framework/wpf/advanced/xaml-overview-wpf) strony.

Po utworzeniu projektu, można go dostosować. Aby to zrobić, wybierz **okno właściwości** z **widoku** menu. Następnie możesz wyświetlić i zmienić opcje elementów projektu, formantów i innych elementów w aplikacji.

::: moniker-end

### <a name="change-the-name-of-mainwindowxaml"></a>Aby zmienić nazwę MainWindow.xaml

Nadajmy MainWindow bardziej szczegółową nazwę.

1. W **Eksploratora rozwiązań**, wybierz opcję *MainWindow.xaml*. Powinien zostać wyświetlony **właściwości** okna, ale jeśli nie wybierz **widoku** menu i następnie **okno właściwości** elementu.

1. Zmiana **nazwy pliku** właściwość `Greetings.xaml`.

     ![Okno właściwości z wyróżnioną nazwą pliku](../media/exploreide-filenameinpropertieswindow.png)

     **Eksplorator rozwiązań** pokazuje, że nazwa pliku jest teraz *Greetings.xaml*, i teraz nosi nazwę pliku zagnieżdżonego kodu *Greetings.xaml.cs*. Ten plik kodu jest zagnieżdżony w *.xaml* węzła pliku, aby pokazać, są ściśle powiązane ze sobą.

## <a name="design-the-user-interface-ui"></a>Zaprojektuj interfejs użytkownika

Zostanie dodany do tej aplikacji trzy typy kontrolek: <xref:System.Windows.Controls.TextBlock> kontrolować dwa <xref:System.Windows.Controls.RadioButton> kontrolek i <xref:System.Windows.Controls.Button> kontroli.

### <a name="add-a-textblock-control"></a>Dodaj formant TextBlock

1. Wprowadź **Ctrl**+**Q** do wywołania **Szybkie uruchamianie** i typ **przybornika**. Wybierz **Widok > przybornika** z listy wyników.

2. W **przybornika**, rozwiń węzeł **wspólnych formantów WPF** węzeł, aby zobaczyć kontrolkę TextBlock.

     ![Przybornik z formantem TextBlock wyróżniony](../media/exploreide-textblocktoolbox.png)

3. Dodaj formant TextBlock na powierzchni projektowej, wybierając **TextBlock** elementu i przeciągając je do okna na powierzchni projektowej. Wyśrodkuj formant w górnej części okna.

Okno powinno wyglądać podobnie, jak na poniższej ilustracji:

![TextBlock — formant w formularzu pozdrowienia](../media/exploreide-greetingswithtextblockonly.png)

Kod znaczników XAML powinien wyglądać podobnie jak w poniższym przykładzie:

```xaml
<TextBlock HorizontalAlignment="Center" TextWrapping="Wrap" VerticalAlignment="Center" RenderTransformOrigin="4.08,2.312" Margin="237,57,221,238"><Run Text="TextBlock"/><InlineUIContainer><TextBlock TextWrapping="Wrap" Text="TextBlock"/>
```

### <a name="customize-the-text-in-the-text-block"></a>Dostosuj tekst w bloku tekstu

1. W widoku XAML zlokalizuj znaczniki TextBlock i zmień atrybut tekstu:

   ```xaml
   Text="Select a message option and then choose the Display button."
   ```

2. Centrum TextBlock ponownie, jeśli to konieczne, a następnie zapisz zmiany, naciśnij klawisze Ctrl + S lub za pomocą **pliku** elementu menu.

Następnie należy dodać dwie [RadioButton](/dotnet/framework/wpf/controls/radiobutton) formantów do formularza.

### <a name="add-radio-buttons"></a>Dodawanie przycisków radiowych

1. W **przybornika**, Znajdź **RadioButton** kontroli.

     ![Okno przybornika z wybraniu kontrolki RadioButton](../media/exploreide-radiobuttontoolbox.png)

2. Dodaj dwa formanty RadioButton do projektowania, surface, wybierając **RadioButton** elementu i przeciągając je do okna na powierzchni projektowej. Przenoszenie przycisków (przez wybranie je i używając klawiszy ze strzałkami) tak, aby przyciski wyświetlane obok siebie pod formantem TextBlock.

     Okno powinno wyglądać następująco:

     ![Formularz pozdrowienia z TextBlock i dwóch przycisków radiowych](../media/exploreide-greetingswithradiobuttons.png)

3. W **właściwości** okna dla lewego formantu RadioButton, zmień **nazwa** właściwości (właściwość w górnej części **właściwości** okna) do `HelloButton`.

     ![Okno właściwości RadioButton](../media/exploreide-buttonproperties.png)

4. W **właściwości** okna dla prawego formantu RadioButton, zmień **nazwa** właściwości `GoodbyeButton`, a następnie zapisz zmiany.

Możesz teraz dodawać wyświetlany tekst dla każdego formantu RadioButton. Następująca procedura aktualizuje **zawartości** właściwości dla kontrolki RadioButton.

### <a name="add-display-text-for-each-radio-button"></a>Dodawać wyświetlany tekst dla każdego przycisku radiowego

1. Wybierz pozycję na powierzchni projektowej Otwórz menu skrótów dla HelloButton naciskając prawym przyciskiem myszy na HelloButton **Edycja tekstu**, a następnie wprowadź `Hello`.

2. Otwórz menu skrótów dla GoodbyeButton naciskając prawym przyciskiem myszy na GoodbyeButton, wybierz opcję **Edycja tekstu**, a następnie wprowadź `Goodbye`.

### <a name="set-a-radio-button-to-be-checked-by-default"></a>Ustaw przycisku radiowego, który ma być sprawdzany domyślnie

W tym kroku skonfigurujemy HelloButton do zaznaczone domyślnie, tak aby zawsze wybrano jeden z przycisków radiowych dwa.

W widoku XAML zlokalizuj znaczniki HelloButton i Dodaj **IsChecked** atrybutu:

```xaml
IsChecked="True"
```

Ostatnim elementem interfejsu użytkownika, jaki dodasz, jest [przycisk](/dotnet/framework/wpf/controls/button) kontroli.

### <a name="add-the-button-control"></a>Dodawanie kontrolki przycisku

1. W **przybornika**, Znajdź **przycisk** sterowania, a następnie dodaj go do powierzchni projektowej, w obszarze formantów RadioButton, przeciągając go do formularza w widoku Projekt.

2. W widoku XAML, zmień wartość **zawartości** dla formantu Button z `Content="Button"` do `Content="Display"`, a następnie zapisz zmiany.

     Znaczniki powinny być podobne do następującego przykładu:   `<Button Content="Display" HorizontalAlignment="Left" VerticalAlignment="Top" Width="75" Margin="215,204,0,0"/>`

     Okno powinno wyglądać podobnie, jak na poniższej ilustracji.

     ![Formularz pozdrowienia z etykietami kontroli](media/exploreide-greetingswithcontrollabels-cs.png)

### <a name="add-code-to-the-display-button"></a>Dodaj kod do przycisku display

Gdy aplikacja jest uruchomiona, okno komunikatu pojawia się po użytkownik wybierze przycisk radiowy, a następnie **wyświetlania** przycisku. Jedno okno komunikatu pojawi się, żeby wyświetlić „Hello”, a inne pojawi się, aby wyświetlić „Goodbye”. Aby utworzyć takie zachowanie, dodasz kod do `Button_Click` zdarzenia w *Greetings.xaml.cs*.

1. Na powierzchni projektowej kliknij dwukrotnie **wyświetlania** przycisku.

     *Greetings.XAML.cs* otworzy, ustaw kursor `Button_Click` zdarzeń.

    ```csharp
    private void Button_Click_1(object sender, RoutedEventArgs e)
    {

    }
    ```

2. Wprowadź następujący kod:

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

3. Zapisz aplikację.

## <a name="debug-and-test-the-application"></a>Debugowanie i testowanie aplikacji

Następnie należy debugować aplikację, aby wyszukać błędy i przetestować, czy oba okna komunikatów wyświetlają się poprawnie. Poniższe instrukcje informujące, jak utworzyć i uruchomić debugera, ale później mogą odczytać [kompilacji aplikacji WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf) i [debugowania WPF](../../debugger/debugging-wpf.md) Aby uzyskać więcej informacji.

### <a name="find-and-fix-errors"></a>Znajdowanie i naprawianie błędów

W tym kroku można znaleźć błędy spowodowane wcześniej, zmieniając nazwę *MainWindow.xaml* pliku.

#### <a name="start-debugging-and-find-the-error"></a>Rozpocznij debugowanie i znaleźć błąd

1. Uruchom debuger, naciskając klawisz **F5** lub wybierając **debugowania**, następnie **Rozpocznij debugowanie**.

   A **trybu przerwania** zostanie wyświetlone okno i **dane wyjściowe** okno wskazuje, że wystąpił IOException: Nie można zlokalizować zasobu 'mainwindow.xaml'.

   ![Zrzut ekranu ioexception — komunikat](../media/exploreide-ioexception.png)

2. Zatrzymaj debuger, wybierając **debugowania** > **Zatrzymaj debugowanie**.

Zmieniliśmy nazwę *MainWindow.xaml* do *Greetings.xaml* na początku tego samouczka, ale kod nadal odwołuje się do *MainWindow.xaml* jako startowy identyfikator URI dla aplikacji, dzięki czemu Nie można uruchomić projektu.

#### <a name="specify-greetingsxaml-as-the-startup-uri"></a>Określić Greetings.xaml jako startowy identyfikator URI

1. W **Eksploratora rozwiązań**, otwórz *App.xaml* pliku.

2. Zmiana `StartupUri="MainWindow.xaml"` do `StartupUri="Greetings.xaml"`, a następnie zapisz zmiany.

Ponownie uruchom debuger (naciśnij klawisz **F5**). Powinien zostać wyświetlony **Greetings** okna aplikacji. Teraz zamknij okna aplikacji, aby zatrzymać debugowanie.

### <a name="debug-with-breakpoints"></a>Debugować z punktami przerwania

Możesz przetestować kod podczas debugowania, dodając kilka punktów przerwania. Możesz dodać punkty przerwania, wybierając **debugowania** > **Przełącz punkt przerwania**, klikając w lewy margines edytora obok wiersza kodu, na którym ma nastąpić przerwanie lub naciskając  **F9**.

#### <a name="add-breakpoints"></a>Dodać punkty przerwania

1. Otwórz *Greetings.xaml.cs*i zaznacz następujący wiersz: `MessageBox.Show("Hello.")`

2. Dodaj punkt przerwania z menu, wybierając **debugowania**, następnie **Przełącz punkt przerwania**.

     Obok wiersza kodu na marginesie po lewej stronie okna edytora jest wyświetlane czerwone koło.

3. Zaznacz następujący wiersz: `MessageBox.Show("Goodbye.")`.

4. Naciśnij klawisz **F9** klawisz, aby dodać punkt przerwania, a następnie naciśnij klawisz **F5** można rozpocząć debugowania.

5. W **Greetings** oknie Wybierz **Hello** przycisk radiowy, a następnie wybierz **wyświetlania** przycisku.

    Wiersz `MessageBox.Show("Hello.")` jest wyróżniony na żółto. W dolnej części IDE, zmiennych automatycznych, zmienne lokalne i obejrzyj są zadokowane razem po lewej stronie, a stos wywołań, punkty przerwania, ustawienia wyjątków, polecenia, bezpośrednie i dane wyjściowe są zadokowane razem po prawej stronie.

    ![Zrzut ekranu przedstawiający punkt przerwania w debugerze](media/exploreide-debugbreakpoint.png)

6. Na pasku menu wybierz **debugowania** > **Step Out**.

     Aplikacja wznawia działanie i pojawia się okno komunikatu z wyraz "Hello".

7. Wybierz **OK** przycisk w oknie komunikatu, aby je zamknąć.

8. W **Greetings** oknie Wybierz **Goodbye** przycisk radiowy, a następnie wybierz **wyświetlania** przycisku.

     Wiersz `MessageBox.Show("Goodbye.")` jest wyróżniony na żółto.

9. Wybierz **F5** klawisz, aby kontynuować debugowanie. Gdy pojawi się okno komunikatu, wybierz **OK** przycisk w oknie komunikatu, aby je zamknąć.

10. Zamknij okno aplikacji, aby zatrzymać debugowanie.

11. Na pasku menu wybierz **debugowania** > **Wyłącz wszystkie punkty przerwania**.

### <a name="build-a-release-version-of-the-application"></a>Tworzenie dystrybucyjnej wersji tej aplikacji

Teraz, gdy upewnieniu się, że wszystko działa, możesz przygotować wersję dystrybucyjną aplikacji.

1. W menu głównym wybierz **kompilacji** > **czyść rozwiązanie** można usunąć pliki pośrednie i pliki wyjściowe, które zostały utworzone podczas poprzednich kompilacji. Nie jest to konieczne, ale go czyści dane wyjściowe z kompilacji debugowania.

2. Zmień konfigurację kompilacji dla HelloWPFApp z **debugowania** do **wersji** za pomocą formantu listy rozwijanej na pasku narzędzi (wyświetlany jest tekst "Debugowanie" obecnie).

3. Skompiluj rozwiązanie, wybierając **kompilacji** > **Kompiluj rozwiązanie**.

Gratulujemy wykonanie kroków tego samouczka! Możesz znaleźć *.exe* utworzone w katalogu rozwiązania i projektu (*...\HelloWPFApp\HelloWPFApp\bin\Release*).

## <a name="see-also"></a>Zobacz także

- [Wskazówki dotyczące produktywności](../../ide/productivity-tips-for-visual-studio.md)