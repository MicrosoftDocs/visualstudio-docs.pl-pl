---
title: 'Przewodnik: tworzenie prostej aplikacji za pomocą języka Visual C# lub Visual Basic | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d5e41dbf3422374add68e351da1e4b703772a3a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "74296861"
---
# <a name="walkthrough-create-a-simple-application-with-visual-c-or-visual-basic"></a>Wskazówki: Tworzenie prostej aplikacji z użyciem Visual C# lub Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wykonując polecenia tego instruktażu, zapoznasz się z wieloma narzędziami, oknami dialogowymi i projektantami używanymi podczas tworzenia aplikacji za pomocą programu Visual Studio. W trakcie poszerzania wiedzy o pracy w zintegrowanym środowisku programistycznym (IDE), stworzysz prostą aplikację w stylu „Hello, World” (Witaj, świecie), zaprojektujesz interfejs użytkownika, dodasz kod i zdebugujesz błędy.

 Ten temat zawiera następujące sekcje:

 [Konfigurowanie IDE](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md#BKMK_ConfigureIDE)

 [Tworzenie prostej aplikacji](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md#BKMK_CreateApp)

 [Debugowanie i testowanie aplikacji](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md#BKMK_DebugTest)

> [!NOTE]
> Ten instruktaż jest oparty na programie Visual Studio Professional. Oferuje on szablon aplikacji WPF, na którym będziesz tworzył projekt z tego instruktażu. Wersja Visual Studio Express for Windows Desktop również oferuje ten szablon, ale wersje Visual Studio Express for Windows i Visual Studio Express for Web go nie mają. Aby uzyskać informacje wprowadzające dotyczące korzystania z Visual Studio Express dla systemu Windows, zobacz [Centrum deweloperów dla aplikacji do sklepu Windows](https://msdn.microsoft.com/windows/apps/br229519). Informacje wprowadzające dotyczące korzystania z Visual Studio Express dla sieci Web znajdują się w temacie [Rozpoczynanie pracy z usługą ASP.NET](https://dotnet.microsoft.com/learn/aspnet/hello-world-tutorial/intro). Ponadto, wersja programu Visual Studio i ustawienia, których używasz, określają nazwy i lokalizacje niektórych elementów interfejsu użytkownika. Zobacz [Dostosowywanie ustawień programistycznych w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="configure-the-ide"></a><a name="BKMK_ConfigureIDE"></a> Konfigurowanie środowiska IDE
 Po uruchomieniu programu Visual Studio po raz pierwszy w programie Visual Studio zostanie wyświetlony komunikat z prośbą o zalogowanie się przy użyciu konta usługi firmy Microsoft (MSA), [Zaloguj się do programu Visual Studio](https://devblogs.microsoft.com/visualstudio/welcome-sign-in-to-visual-studio/). Nie musisz się zalogować i możesz zrobić to później.

 W przypadku uruchamiania programu Visual Studio należy wybrać kombinację ustawień, która stosuje zestaw wstępnie zdefiniowanych dostosowań do IDE. Każda kombinacja ustawień została zaprojektowana w celu ułatwienia tworzenia aplikacji.

 W tym instruktażu przyjęto założenie, że zastosowano **Ogólne ustawienia programowania**, które stosuje najmniej dostosowanie do IDE. Jeśli wybrano już język C# lub Visual Basic (obie opcje są dobrane), nie trzeba zmieniać ustawień.  Jeśli chcesz zmienić ustawienia, możesz użyć **Kreatora importowania i eksportowania ustawień**. Zobacz [Dostosowywanie ustawień programistycznych w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 Po otwarciu programu Visual Studio widzisz okna narzędzi, menu i paski narzędzi oraz przestrzeń głównego okna. Okna narzędzi są zadokowane po lewej i prawej stronie okna aplikacji, z **szybkim uruchamianiem**, paskiem menu i standardowym paskiem narzędzi u góry. Na środku okna aplikacji znajduje się **Strona Start**. Podczas ładowania rozwiązania lub projektu, Edytory i projektanci pojawiają się w miejscu, w którym znajduje się **Strona początkowa** . Podczas opracowywania aplikacji spędzisz większość czasu w tym środkowym obszarze.

 Rysunek 2: Visual Studio IDE

 ![Środowisko IDE z zastosowaniem ustawień ogólnych](../ide/media/exploreide-idewithgeneralsettings.png "ExploreIDE-IDEwithgeneralsettings")

 Możesz dokonać dodatkowych dostosowań w programie Visual Studio, takich jak zmiana kroju czcionki i rozmiaru tekstu w edytorze lub motywu kolorów IDE, za pomocą okna dialogowego **Opcje** . W zależności od kombinacji ustawień, które zostały już zastosowane, niektóre elementy w tym oknie dialogowym mogą nie być automatycznie widoczne. Można upewnić się, że wszystkie możliwe opcje są wyświetlane, zaznaczając pole wyboru **Pokaż wszystkie ustawienia** .

 Rysunek 3: Okno dialogowe Opcje

 ![Okno dialogowe Opcje wirh Pokaż wszystkie ustawienia opcja](../ide/media/exploreide-optionsdialogbox.png "ExploreIDE-Optionsdialogbox")

 W tym przykładzie zmienisz motyw kolorów IDE z jasnego na ciemny.  Możesz przejść z wyprzedzeniem, aby utworzyć projekt.

#### <a name="to-change-the-color-theme-of-the-ide"></a>Aby zmienić motyw kolorów IDE.

1. Otwórz okno dialogowe **Opcje** , wybierając menu **Narzędzia** u góry, a następnie **Opcje...** elementów.

    ![Opcje polecenie w menu Narzędzia](../ide/media/exploreide-toolsoptionsmenu.png "ExploreIDE-ToolsOptionsmenu")

2. Zmień **motyw kolorów** na **ciemny**, a następnie kliknij przycisk **OK**.

    ![Wybrany motyw ciemny kolor](../ide/media/exploreide-darkthemeoptionsdlgbox.png "ExploreIDE-Darkthemeoptionsdlgbox")

   Kolory w programie Visual Studio powinny odpowiadać następującemu obrazowi:

   ![Środowisko IDE z zastosowanym motywem ciemnym](../ide/media/exploreide-darkthemeide.png "ExploreIDE-DarkThemeIDE")

   Motyw kolorów używany do obrazów w pozostałej części tego instruktażu jest motywem jasnym. Aby uzyskać więcej informacji na temat dostosowywania środowiska IDE, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="create-a-simple-application"></a><a name="BKMK_CreateApp"></a> Tworzenie prostej aplikacji

### <a name="create-the-project"></a>Tworzenie projektu
 Podczas tworzenia aplikacji w programie Visual Studio, należy najpierw utworzyć projekt i rozwiązanie. Na potrzeby tego przykładu utworzysz projekt Windows Presentation Foundation (WPF).

##### <a name="to-create-the-wpf-project"></a>Aby utworzyć projekt WPF

1. Tworzenie nowego projektu. Na pasku menu wybierz **plik**, **Nowy**, **projekt...**.

    ![Na pasku menu wybierz kolejno opcje plik, nowy, projekt.](../ide/media/exploreide-filenewproject.png "ExploreIDE-FileNewProject")

    Możesz też wpisać **Nowy projekt** w polu **Szybkie uruchamianie** , aby zrobić to samo.

    ![W polu Szybkie uruchamianie określ nowy projekt](../ide/media/exploreide-quicklaunchnewprojectsmall.png "ExploreIDE-QuickLaunchNewProjectsmall")

2. Wybierz Visual Basic lub szablon aplikacji WPF języka Visual C#, wybierając w lewym okienku **zainstalowane**, **Szablony**, **Visual C#**, **Windows**, a następnie wybierając pozycję Aplikacja WPF w środkowym okienku.  Nazwij projekt HelloWPFApp w dolnej części okna dialogowego Nowy projekt.

    ![Utwórz projekt Visual Basic WPF, HelloWPFApp](../ide/media/exploreide-newprojectvb.png "ExploreIDE-NewProjectVB")

    LUB

    ![Utwórz projekt Visual C&#35; WPF, HelloWPFApp](../ide/media/exploreide-newprojectcsharp.png "ExploreIDE-NewProjectcsharp")

   Program Visual Studio tworzy projekt i rozwiązanie HelloWPFApp, a **Eksplorator rozwiązań** wyświetla różne pliki. Projektant WPF przedstawia widok projektu i widok XAML MainWindow. XAML w widoku złożonym. Można przesuwać rozdzielacz, aby pokazać więcej lub mniej jednego widoku.  Możesz zobaczyć tylko widok wizualizacji lub tylko widok XAML. (Aby uzyskać więcej informacji, zobacz [WPF Designer dla Windows Forms deweloperów](https://msdn.microsoft.com/47ad0909-e89b-4996-b4ac-874d929f94ca)). Następujące elementy są wyświetlane w **Eksplorator rozwiązań**:

   Rysunek 5: Elementy projektu

   ![Eksplorator rozwiązań z załadowanymi plikami HelloWPFApp](../ide/media/exploreide-hellowpfappfiles.png "ExploreIDE-HelloWPFAppFiles")

   Po utworzeniu projektu, można go dostosować. Za pomocą okna **Właściwości** (dostępnego w menu **Widok** ), można wyświetlić i zmienić opcje elementów projektu, formantów i innych elementów w aplikacji. Za pomocą właściwości projektu i stron właściwości, można wyświetlić i zmienić opcje dla projektów i rozwiązań.

##### <a name="to-change-the-name-of-mainwindowxaml"></a>Aby zmienić nazwę MainWindow.xaml

1. W poniższej procedurze nadasz bardziej szczegółową nazwę obiektowi MainWindow. W **Eksplorator rozwiązań**wybierz pozycję MainWindow. XAML. Powinno zostać wyświetlone okno **Właściwości** , ale jeśli nie, wybierz menu **Widok** i element **okna właściwości** . Zmień właściwość **Nazwa pliku** na `Greetings.xaml` .

    ![okno Właściwości z wyróżnioną nazwą pliku](../ide/media/exploreide-filenameinpropertieswindow.png "ExploreIDE-FilenameinPropertiesWindow")

    **Eksplorator rozwiązań** pokazuje, że nazwa pliku to teraz Greetings. XAML, a po rozwinięciu węzła MainWindow. XAML (poprzez umieszczenie fokusu w węźle i naciśnięcie klawisza rightarrow), zobaczysz nazwę MainWindow. XAML. vb lub MainWindow.XAML.cs jest teraz Greetings. XAML. vb lub Greetings.XAML.cs. Ten plik kodu jest zagnieżdżony w węźle pliku. XAML, aby pokazać, że są one ściśle powiązane ze sobą.

   > [!WARNING]
   > Ta zmiana powoduje wystąpienie błędu. Na dalszym etapie dowiesz się, jak go debugować i naprawiać.

2. W **Eksplorator rozwiązań**otwórz Greetings. XAML w widoku projektanta (naciskając klawisz ENTER, gdy węzeł ma fokus) i wybierz pasek tytułu okna przy użyciu myszy.

3. W oknie **Właściwości** Zmień wartość właściwości **tytuł** na `Greetings` .

   Na pasku tytułu MainWindow.xaml pojawia się teraz napis „Greetings”.

### <a name="design-the-user-interface-ui"></a>Zaprojektuj interfejs użytkownika
 Dodamy w tej aplikacji trzy typy kontrolek: kontrolkę TextBlock (blok tekstu), dwie kontrolki RadioButton (przycisk radiowy) i kontrolkę Button (przycisk).

##### <a name="to-add-a-textblock-control"></a>Aby dodać kontrolkę TextBlock

1. Otwórz okno **Przybornik** , wybierając menu **Widok** i element **Przybornik** .

2. W **przyborniku**wyszukaj formant TextBlock.

    ![Przybornik z wyróżnioną kontrolką TextBlock](../ide/media/exploreide-textblocktoolbox.png "ExploreIDE-TextBlockToolbox")

3. Dodaj kontrolkę TextBlock do powierzchni projektowej, wybierając element TextBlock i przeciągając go do okna na powierzchni projektowej.  Wyśrodkuj formant w górnej części okna.

   Okno powinno wyglądać podobnie, jak na poniższej ilustracji:

   Rysunek 7: Okno pozdrowień Greetings z formantem TextBlock

   ![Kontrolka TextBlock w formularzu Greetings](../ide/media/exploreide-greetingswithtextblockonly.png "ExploreIDE-GreetingswithTextblockonly")

   Znacznik XAML powinien wyglądać mniej więcej tak:

```
<TextBlock HorizontalAlignment="Center" TextWrapping="Wrap" VerticalAlignment="Center" RenderTransformOrigin="4.08,2.312" Margin="237,57,221,238"><Run Text="TextBlock"/><InlineUIContainer><TextBlock TextWrapping="Wrap" Text="TextBlock"/>
```

##### <a name="to-customize-the-text-in-the-text-block"></a>Aby dostosować tekst w bloku tekstowym

1. W widoku XAML Znajdź znaczniki TextBlock i Zmień atrybut text: `Text=”Select a message option and then choose the Display button.”`

2. Jeśli element TextBlock nie zostanie rozwinięty w celu dopasowania go do widok Projekt, Powiększ kontrolkę TextBlock (przy użyciu uchwytów dojścia do krawędzi), aby wyświetlić cały tekst.

3. Zapisz zmiany, naciskając klawisze Ctrl-s lub korzystając z elementu menu **plik** .

   Następnie dodasz dwie kontrolki [RadioButton](https://msdn.microsoft.com/library/6c9ba847-eab7-4bba-9c74-6b56ef72067b) do formularza.

##### <a name="to-add-radio-buttons"></a>Aby dodać przyciski radiowe

1. W **przyborniku**wyszukaj formant RadioButton.

    ![Okno przybornika z wybraną kontrolką RadioButton](../ide/media/exploreide-radiobuttontoolbox.png "ExploreIDE-RadioButtonToolbox")

2. Dodaj dwa kontrolki RadioButton do powierzchni projektowej, wybierając element RadioButton i przeciągając go do okna na powierzchni projektowej dwa razy, a następnie przenieś przyciski (wybierając je i używając klawiszy strzałek), aby przyciski były widoczne obok kontrolki TextBlock.

    Okno powinno wyglądać następująco:

    Rysunek 8: Przyciski radiowe w oknie Greetings.

    ![Formularze Greetings z elementami TextBlock i dwoma elementami RadioButton](../ide/media/exploreide-greetingswithradiobuttons.png "ExploreIDE-Greetingswithradiobuttons")

3. W oknie **Właściwości** dla lewego formantu RadioButton, Zmień właściwość **name** (właściwość w górnej części okna **Właściwości** ) na `RadioButton1` .  Upewnij się, że wybrano element RadioButton, a nie siatkę tła w formularzu; pole Typ okna właściwości w polu Nazwa powinno powiedzieć RadioButton.

4. W oknie **Właściwości** dla prawego formantu RadioButton, Zmień właściwość **Nazwa** na `RadioButton2` , a następnie Zapisz zmiany przez naciśnięcie klawiszy Ctrl-s lub przy użyciu elementu menu **plik** .  Przed zmianą i zapisaniem upewnij się, że został wybrany element RadioButton.

   Możesz teraz dodawać wyświetlany tekst dla każdego formantu RadioButton. Poniższa procedura umożliwia zaktualizowanie właściwości **Content** dla kontrolki RadioButton.

##### <a name="to-add-display-text-for-each-radio-button"></a>Aby dodać wyświetlany tekst dla każdego przycisku radiowego

1. Na powierzchni projektowej Otwórz menu skrótów dla RadioButton1, naciskając prawy przycisk myszy podczas wybierania RadioButton1, wybierz polecenie **Edytuj tekst**, a następnie wprowadź `Hello` .

2. Otwórz menu skrótów dla RadioButton2, naciskając prawy przycisk myszy, wybierając pozycję RadioButton2, wybierz polecenie **Edytuj tekst**, a następnie wprowadź `Goodbye` .

   Ostatnim elementem interfejsu użytkownika, który dodasz, jest kontrolka [przycisku](https://msdn.microsoft.com/library/a9d8f5a5-c98c-463e-808a-5a4e63173098) .

##### <a name="to-add-the-button-control"></a>Aby dodać kontrolkę przycisku

1. W **przyborniku**wyszukaj formant **Button** , a następnie dodaj go do powierzchni projektowej w obszarze kontrolki RadioButton, wybierając przycisk i przeciągając go do formularza w widoku projektu.

2. W widoku XAML Zmień wartość **zawartości** kontrolki Button z `Content=”Button”` na `Content=”Display”` , a następnie Zapisz zmiany (Ctrl-s lub użyj menu **plik** ).

    Znacznik powinien wyglądać podobnie do poniższego przykładu: `<Button Content="Display" HorizontalAlignment="Left" VerticalAlignment="Top" Width="75" Margin="215,204,0,0"/>`

   Okno powinno wyglądać podobnie, jak na poniższej ilustracji.

   Rysunek 9: Końcowy interfejs użytkownika Greetings

   ![Formularz pozdrowienia z etykietami kontrolki](../ide/media/exploreide-greetingswithconrollabels.png "ExploreIDE-Greetingswithconrollabels")

### <a name="add-code-to-the-display-button"></a>Dodaj kod do przycisku Display
 Gdy aplikacja jest uruchomiona, okno komunikatu pojawia się, gdy użytkownik najpierw wybierze przycisk radiowy, a następnie wybierze przycisk **wyświetlania** . Jedno okno komunikatu pojawi się, żeby wyświetlić „Hello”, a inne pojawi się, aby wyświetlić „Goodbye”. Aby uzyskać takie zachowanie, dodasz kod do zdarzenia Button_Click w Greetings.xaml.vb lub Greetings.xaml.cs.

##### <a name="add-code-to-display-message-boxes"></a>Dodaj kod do wyświetlania okien komunikatów

1. Na powierzchni projektowej kliknij dwukrotnie przycisk **Wyświetl** .

     Greetings.xaml.vb lub Greetings.xaml.cs otworzy się, kursor będzie się znajdował w zdarzeniu Button_Click. Możesz również dodać program obsługi zdarzeń kliknięcia w następujący sposób (jeśli wklejony kod ma czerwoną literę w obszarze dowolnych nazw, prawdopodobnie nie wybrano kontrolki RadioButton na powierzchni projektowej i zmień ich nazwy):

     Dla języka Visual Basic zdarzenie obsługi powinno wyglądać następująco:

    ```vb
    Private Sub Button_Click_1(sender As Object, e As RoutedEventArgs)

    End Sub
    ```

     Dla języka Visual C# zdarzenie obsługi powinno wyglądać następująco:

    ```csharp
    private void Button_Click_1(object sender, RoutedEventArgs e)
    {

    }
    ```

2. Dla języka Visual Basic wprowadź następujący kod:

    ```vb
    If RadioButton1.IsChecked = True Then
        MessageBox.Show("Hello.")
    Else RadioButton2.IsChecked = True
        MessageBox.Show("Goodbye.")
    End If

    ```

     Dla języka Visual# wprowadź następujący kod:

    ```
    if (RadioButton1.IsChecked == true)
    {
        MessageBox.Show("Hello.");
    }
    else
    {
        RadioButton2.IsChecked = true;
        MessageBox.Show("Goodbye.");
    }
    ```

3. Zapisz aplikację.

## <a name="debug-and-test-the-application"></a><a name="BKMK_DebugTest"></a> Debugowanie i testowanie aplikacji
 Następnie należy debugować aplikację, aby wyszukać błędy i przetestować, czy oba okna komunikatów wyświetlają się poprawnie. Poniższe instrukcje przedstawiają sposób kompilowania i uruchamiania debugera, ale później można zapoznać się [z tworzeniem aplikacji WPF (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c) i [debugowaniem WPF](../debugger/debugging-wpf.md) , aby uzyskać więcej informacji.

### <a name="find-and-fix-errors"></a>Znajdowanie i naprawianie błędów
 W tym kroku można znaleźć błędy spowodowane wcześniej przez zmianę nazwy okna głównego pliku XAML.

##### <a name="to-start-debugging-and-find-the-error"></a>Aby rozpocząć debugowanie i znaleźć błąd

1. Uruchom Debuger, wybierając **Debuguj**, a następnie **Rozpocznij debugowanie**.

    ![Rozpocznij debugowanie polecenia w menu Debugowanie](../ide/media/exploreide-startdebugging.png "ExploreIDE-StartDebugging")

    Zostanie wyświetlone okno dialogowe, wskazując, że wystąpił IOException: nie można zlokalizować zasobu 'mainwindow.xaml'.

2. Wybierz przycisk **OK** , a następnie Zatrzymaj debuger.

    ![Polecenie zatrzymania debugowania w menu Debugowanie](../ide/media/exploreide-stopdebugging.png "ExploreIDE-StopDebugging")

   Zmieniono nazwę MainWindow. XAML na Greetings. XAML na początku tego instruktażu, ale kod nadal odwołuje się do MainWindow. XAML jako startowy identyfikator URI dla aplikacji, więc nie można uruchomić projektu.

##### <a name="to-specify-greetingsxaml-as-the-startup-uri"></a>Aby określić Greetings.xaml jako startowy identyfikator URI

1. W **Eksplorator rozwiązań**Otwórz plik App. XAML (w projekcie C#) lub plik Application. XAML (w Visual Basic projekcie) w widoku XAML (nie można go otworzyć w widok Projekt), wybierając plik i naciskając klawisz ENTER lub klikając go dwukrotnie.

2. Zmień `StartupUri="MainWindow.xaml"` na `StartupUri="Greetings.xaml"` , a następnie Zapisz zmiany za pomocą klawiszy Ctrl-s.

   Ponownie uruchom debuger (naciśnij klawisz F5). Powinieneś zobaczyć okno powitania aplikacji.

### <a name="to-debug-with-breakpoints"></a>Aby debugować z punktami przerwania
 Dodając kilka punktów przerwania, można przetestować kod podczas debugowania. Możesz dodać punkty przerwania, wybierając pozycję **Debuguj** w menu głównym, a następnie **Przełącz punkt przerwania** lub klikając na lewym marginesie edytora obok wiersza kodu, w którym ma nastąpić przerwanie.

##### <a name="to-add-breakpoints"></a>Aby dodać punkty przerwania

1. Otwórz Greetings. XAML. vb lub Greetings.xaml.cs i zaznacz następujący wiersz: `MessageBox.Show("Hello.")`

2. Dodaj punkt przerwania z menu, wybierając **Debuguj**, a następnie **Przełącz punkt przerwania**.

     ![Przełącz polecenie punktu przerwania w menu Debugowanie](../ide/media/exploreide-togglebreakpoint.png "ExploreIDE — Togglebreakpoint —")

     Obok wiersza kodu na marginesie po lewej stronie okna edytora jest wyświetlane czerwone koło.

3. Wybierz następujący wiersz: `MessageBox.Show("Goodbye.")` .

4. Naciśnij klawisz F9, aby dodać punkt przerwania, a następnie naciśnij klawisz F5, aby rozpocząć debugowanie.

5. W oknie **Greetings** wybierz przycisk radiowy **Hello** , a następnie wybierz przycisk **Wyświetl** .

     Wiersz `MessageBox.Show("Hello.")` jest wyróżniony kolorem żółtym. W dolnej części środowiska IDE okna Autostart, lokalne i czujki są zadokowane po lewej stronie, a stos wywołań, punkty przerwania, polecenia, natychmiastowe i wyjściowe okna są zadokowane razem po prawej stronie.

6. Na pasku menu wybierz **Debuguj**, **Wyjdź**.

     Aplikacja wznawia działanie i pojawia się okno komunikatu z napisem „Hello”.

7. Wybierz przycisk **OK** w oknie komunikatu, aby je zamknąć.

8. W oknie **Greetings** wybierz przycisk radiowy **pożegnanie** , a następnie wybierz przycisk **Wyświetl** .

     Wiersz `MessageBox.Show("Goodbye.")` jest wyróżniony kolorem żółtym.

9. Wciśnij klawisz F5, aby kontynuować debugowanie. Gdy pojawi się okno komunikatu, wybierz przycisk **OK** w oknie komunikatu, aby je zamknąć.

10. Naciśnij klawisze SHIFT + F5 (naciśnij klawisz Shift) i przytrzymując go, naciśnij klawisz F5, aby zatrzymać debugowanie.

11. Na pasku menu wybierz **Debuguj**, **Wyłącz wszystkie punkty przerwania**.

### <a name="build-a-release-version-of-the-application"></a>Tworzenie dystrybucyjnej wersji tej aplikacji
 Teraz, gdy masz już pewność, że wszystko działa, możesz przygotować wersję dystrybucyjną aplikacji.

##### <a name="to-clean-the-solution-files-and-build-a-release-version"></a>Aby wyczyścić pliki rozwiązań i zbudować wersję przeznaczoną do publikacji

1. W menu głównym wybierz pozycję **kompilacja**, a następnie **Wyczyść rozwiązanie** , aby usunąć pliki pośrednie i pliki wyjściowe, które zostały utworzone podczas poprzednich kompilacji.  Nie jest to konieczne, ale czyści dane wyjściowe kompilacji debugowania.

    ![Polecenie Oczyść rozwiązanie w menu Kompilacja](../ide/media/exploreide-cleansolution.png "ExploreIDE-CleanSolution")

2. Zmień konfigurację kompilacji dla HelloWPFApp z **Debug** na **Release** przy użyciu kontrolki menu rozwijanego na pasku narzędzi (jest to komunikat "Debugowanie" jest obecnie).

    ![Standardowy pasek narzędzi z wybraną wersją](../ide/media/exploreide-releaseversion.png "ExploreIDE-ReleaseVersion")

3. Skompiluj rozwiązanie, wybierając pozycję **kompilacja**, a następnie **Skompiluj rozwiązanie** lub naciśnij klawisz F6.

    ![Kompiluj polecenie rozwiązania w menu Kompilacja](../ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")

   Gratulujemy zakończenia instruktażu! Można znaleźć plik. exe, który został utworzony w ramach rozwiązania i katalogu projektu (. ..\HelloWPFApp\HelloWPFApp\bin\Release \\ ). Jeśli chcesz poznać więcej przykładów, zobacz [Visual Studio Samples](../ide/visual-studio-samples.md).

## <a name="see-also"></a>Zobacz też
 [Co nowego w programie Visual studio 2015](../what-s-new-in-visual-studio-2015.md) [wprowadzenie do programowania przy użyciu](../ide/get-started-developing-with-visual-studio.md) [porad dotyczących produktywności](../ide/productivity-tips-for-visual-studio.md) programu Visual Studio
