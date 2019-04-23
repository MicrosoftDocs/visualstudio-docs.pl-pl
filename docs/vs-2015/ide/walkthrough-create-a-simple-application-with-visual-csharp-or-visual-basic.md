---
title: 'Przewodnik: Tworzenie prostej aplikacji z wizualizacją C# lub Visual Basic | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5286f79f55f2a09122fb551911162bd609ce3bb2
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60040562"
---
# <a name="walkthrough-create-a-simple-application-with-visual-c-or-visual-basic"></a>Przewodnik: Tworzenie prostej aplikacji z wizualizacją C# lub Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wykonując polecenia tego instruktażu, zapoznasz się z wieloma narzędziami, oknami dialogowymi i projektantami używanymi podczas tworzenia aplikacji za pomocą programu Visual Studio. W trakcie poszerzania wiedzy o pracy w zintegrowanym środowisku programistycznym (IDE), stworzysz prostą aplikację w stylu „Hello, World” (Witaj, świecie), zaprojektujesz interfejs użytkownika, dodasz kod i zdebugujesz błędy.  
  
 Ten temat zawiera następujące sekcje:  
  
 [Konfigurowanie IDE](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md#BKMK_ConfigureIDE)  
  
 [Tworzenie prostej aplikacji](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md#BKMK_CreateApp)  
  
 [Debugowanie i testowanie aplikacji](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md#BKMK_DebugTest)  
  
> [!NOTE]
>  Ten instruktaż jest oparty na programie Visual Studio Professional. Oferuje on szablon aplikacji WPF, na którym będziesz tworzył projekt z tego instruktażu. Wersja Visual Studio Express for Windows Desktop również oferuje ten szablon, ale wersje Visual Studio Express for Windows i Visual Studio Express for Web go nie mają. Aby uzyskać wprowadzające informacje o sposobie używania programu Visual Studio Express for Windows, zobacz [Centrum rozwoju aplikacji Windows Store](http://msdn.microsoft.com/windows/apps/br229519). Aby uzyskać wprowadzające informacje o sposobie używania programu Visual Studio Express for Web, zobacz [wprowadzenie do programu ASP.NET](http://www.asp.net/get-started). Ponadto, wersja programu Visual Studio i ustawienia, których używasz, określają nazwy i lokalizacje niektórych elementów interfejsu użytkownika. Zobacz [Dostosowywanie ustawień środowiska deweloperskiego w programie Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="BKMK_ConfigureIDE"></a> Konfigurowanie IDE  
 Po uruchomieniu programu Visual Studio po raz pierwszy, Visual Studio wyświetli monit do logowania się przy użyciu konta usługi Microsoft (MSA), [Zaloguj się do programu Visual Studio](http://blogs.msdn.com/b/visualstudio/archive/2013/06/28/welcome-sign-in-to-visual-studio.aspx). Nie trzeba logować się i można później.  
  
 Na uruchamiania programu Visual Studio następnie należy wybrać kombinację ustawień, która wprowadza zestaw predefiniowanych dostosowań do IDE. Każda kombinacja ustawień została zaprojektowana w celu ułatwienia tworzenia aplikacji.  
  
 W tym przewodniku przyjęto założenie, możesz zastosować **ogólnych ustawieniach projektowych**, co ma zastosowanie najmniejsza ilość zmian IDE. Jeśli zostały już wybrane, C# lub Visual Basic (obie to dobrych wyborów), nie trzeba zmienić ustawienia.  Jeśli chcesz zmienić swoje ustawienia, można użyć **Kreatora importowania i eksportowania ustawień**. Zobacz [Dostosowywanie ustawień środowiska deweloperskiego w programie Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Po otwarciu programu Visual Studio widzisz okna narzędzi, menu i paski narzędzi oraz przestrzeń głównego okna. Okna narzędzi są zadokowane po lewej i prawej stronie okna aplikacji za pomocą **Szybkie uruchamianie**, pasek menu i standardowy pasek narzędzi u góry. Na środku okna aplikacji znajduje **strona startowa**. Podczas ładowania rozwiązania lub projektu, edytory i projektanty są wyświetlane w miejscu gdzie **strona startowa** jest. Podczas opracowywania aplikacji spędzisz większość czasu w tym środkowym obszarze.  
  
 Rysunek 2: Visual Studio IDE  
  
 ![Środowisko IDE z zastosowaniem ustawień ogólnych](../ide/media/exploreide-idewithgeneralsettings.png "ExploreIDE IDEwithgeneralsettings")  
  
 Możesz przeprowadzić dodatkowe dostosowania do programu Visual Studio, takie jak zmiana krój czcionki i rozmiar tekstu w edytorze lub motyw kolorów IDE, za pomocą **opcje** okno dialogowe. W zależności od kombinacji ustawień, które zostały już zastosowane, niektóre elementy w tym oknie dialogowym mogą nie być automatycznie widoczne. Możesz upewnić się, że wszystkie możliwe opcje są widoczne, zaznaczając **Pokaż wszystkie ustawienia** pole wyboru.  
  
 Rysunek 3: Opcje — Okno dialogowe  
  
 ![Wirh okno dialogowe opcji Pokaż wszystkie ustawienia opcji](../ide/media/exploreide-optionsdialogbox.png "ExploreIDE Optionsdialogbox")  
  
 W tym przykładzie zmienisz motyw kolorów IDE z jasnego na ciemny.  Możesz przejść od razu, jeśli chcesz utworzyć projekt.  
  
#### <a name="to-change-the-color-theme-of-the-ide"></a>Aby zmienić motyw kolorów IDE.  
  
1. Otwórz **opcje** okno dialogowe, wybierając **narzędzia** menu u góry i następnie **opcje...** element.  
  
    ![Opcje polecenia w menu narzędzia](../ide/media/exploreide-toolsoptionsmenu.png "ExploreIDE ToolsOptionsmenu")  
  
2. Zmiana **motyw kolorów** do **ciemny**, następnie kliknij przycisk **OK**.  
  
    ![Ciemnego motywu kolorystycznego wybrane](../ide/media/exploreide-darkthemeoptionsdlgbox.png "ExploreIDE Darkthemeoptionsdlgbox")  
  
   Kolory w programie Visual Studio powinny odpowiadać następującemu obrazowi:  
  
   ![Środowisko IDE z motywu ciemny stosowane](../ide/media/exploreide-darkthemeide.png "ExploreIDE DarkThemeIDE")  
  
   Motywem kolorów używanym dla obrazów w pozostałej części tego instruktażu jest jasny motyw. Aby uzyskać więcej informacji o dostosowywaniu środowiska IDE, zobacz [Dostosowywanie ustawień środowiska deweloperskiego, w programie Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="BKMK_CreateApp"></a> Tworzenie prostej aplikacji  
  
### <a name="create-the-project"></a>Utwórz projekt  
 Podczas tworzenia aplikacji w programie Visual Studio, należy najpierw utworzyć projekt i rozwiązanie. W tym przykładzie utworzysz projekt Windows Presentation Foundation (WPF).  
  
##### <a name="to-create-the-wpf-project"></a>Aby utworzyć projekt WPF  
  
1. Utwórz nowy projekt. Na pasku menu wybierz **pliku**, **New**, **projektu...** .  
  
    ![Na pasku menu wybierz kolejno opcje Plik, nowe, projektów](../ide/media/exploreide-filenewproject.png "ExploreIDE FileNewProject")  
  
    Możesz również wpisać **nowy projekt** w **Szybkie uruchamianie** pole, aby zrobić to samo.  
  
    ![W polu Szybkie uruchamianie określ nowy projekt](../ide/media/exploreide-quicklaunchnewprojectsmall.png "ExploreIDE QuickLaunchNewProjectsmall")  
  
2. Wybierz pozycję Visual Basic lub Visual C# WPF Application szablon, wybierając w okienku po lewej stronie **zainstalowane**, **szablony**, **Visual C#**, **Windows**, na przykład, a następnie wybierając aplikacji WPF w środkowym okienku.  Nazwę projektu HelloWPFApp w dolnej części okna dialogowego Nowy projekt.  
  
    ![Utwórz projekt WPF języka Visual Basic, HelloWPFApp](../ide/media/exploreide-newprojectvb.png "ExploreIDE NewProjectVB")  
  
    LUB  
  
    ![Utwórz Visual C&#35; projekt WPF, HelloWPFApp](../ide/media/exploreide-newprojectcsharp.png "ExploreIDE NewProjectcsharp")  
  
   Program Visual Studio tworzy projekt i rozwiązanie HelloWPFApp i **Eksploratora rozwiązań** pokazuje różne pliki. Projektant WPF Pokazuje widok projektu i widok XAML pliku mainwindow.XAML w widoku podzielonym. Przesuń, rozdzielacza, aby wyświetlić więcej lub mniej albo widoku.  Można wyświetlić tylko visual widoku lub w widoku XAML. (Aby uzyskać więcej informacji, zobacz [WPF Designer for Windows formularzy deweloperów](http://msdn.microsoft.com/47ad0909-e89b-4996-b4ac-874d929f94ca)). Następujące elementy są wyświetlane w **Eksploratora rozwiązań**:  
  
   Rysunek 5: Elementy projektu  
  
   ![Załadowany w Eksploratorze rozwiązań z plikami HelloWPFApp](../ide/media/exploreide-hellowpfappfiles.png "ExploreIDE HelloWPFAppFiles")  
  
   Po utworzeniu projektu, można go dostosować. Za pomocą **właściwości** okna (znalezione na **widoku** menu), można wyświetlić i zmienić opcje elementów projektu, formantów i innych elementów w aplikacji. Za pomocą właściwości projektu i stron właściwości, można wyświetlić i zmienić opcje dla projektów i rozwiązań.  
  
##### <a name="to-change-the-name-of-mainwindowxaml"></a>Aby zmienić nazwę MainWindow.xaml  
  
1. W poniższej procedurze nadasz bardziej szczegółową nazwę obiektowi MainWindow. W **Eksploratora rozwiązań**, wybierz opcję MainWindow.xaml. Powinien zostać wyświetlony **właściwości** okna, ale jeśli nie wybierz **widoku** menu i **okno właściwości** elementu. Zmiana **nazwy pliku** właściwość `Greetings.xaml`.  
  
    ![Okno właściwości z wyróżnioną nazwą pliku](../ide/media/exploreide-filenameinpropertieswindow.png "ExploreIDE FilenameinPropertiesWindow")  
  
    **Eksplorator rozwiązań** wskazują, że nazwa pliku to teraz Greetings.xaml, i po rozwinięciu węzła MainWindow.xaml (przez umieszczenie fokus w węźle, a następnie naciskając klawisz Strzałka w prawo), możesz zobaczyć nazwę tego pliku MainWindow.xaml.vb lub MainWindow.xaml.cs to teraz Greetings.XAML.VB lub Greetings.xaml.cs. Ten plik kodu jest zagnieżdżony w węźle plik .xaml, aby pokazać, że są one ściśle powiązane ze sobą.  
  
   > [!WARNING]
   >  Ta zmiana powoduje wystąpienie błędu. Na dalszym etapie dowiesz się, jak go debugować i naprawiać.  
  
2. W **Eksploratora rozwiązań**, otwórz Greetings.xaml w widoku Projektanta (przez naciśnięcie klawisza Enter, gdy węzeł ma fokus) i wybierz pasek tytułu okna za pomocą myszy.  
  
3. W **właściwości** okna, zmień wartość właściwości **tytuł** właściwość `Greetings`.  
  
   Na pasku tytułu MainWindow.xaml pojawia się teraz napis „Greetings”.  
  
### <a name="design-the-user-interface-ui"></a>Zaprojektuj interfejs użytkownika  
 Dodamy w tej aplikacji trzy typy kontrolek: kontrolkę TextBlock (blok tekstu), dwie kontrolki RadioButton (przycisk radiowy) i kontrolkę Button (przycisk).  
  
##### <a name="to-add-a-textblock-control"></a>Aby dodać kontrolkę TextBlock  
  
1. Otwórz **przybornika** okna, wybierając **widoku** menu i **przybornika** elementu.  
  
2. W **przybornika**, wyszukaj formant TextBlock.  
  
    ![Przybornik z formantem TextBlock wyróżnione](../ide/media/exploreide-textblocktoolbox.png "ExploreIDE TextBlockToolbox")  
  
3. Dodaj formant TextBlock na powierzchni projektowej, wybierając element TextBlock i przeciągając je do okna na powierzchni projektowej.  Wyśrodkuj formant w górnej części okna.  
  
   Okno powinno wyglądać podobnie, jak na poniższej ilustracji:  
  
   Rysunek 7: Okno pozdrowień Greetings z formantem TextBlock  
  
   ![TextBlock — formant w formularzu Greetings](../ide/media/exploreide-greetingswithtextblockonly.png "ExploreIDE GreetingswithTextblockonly")  
  
   Znacznik XAML powinien wyglądać mniej więcej tak:  
  
```  
<TextBlock HorizontalAlignment="Center" TextWrapping="Wrap" VerticalAlignment="Center" RenderTransformOrigin="4.08,2.312" Margin="237,57,221,238"><Run Text="TextBlock"/><InlineUIContainer><TextBlock TextWrapping="Wrap" Text="TextBlock"/>  
```  
  
##### <a name="to-customize-the-text-in-the-text-block"></a>Aby dostosować tekst w bloku tekstowym  
  
1. W widoku XAML zlokalizuj znaczniki TextBlock i zmień atrybut tekstu: `Text=”Select a message option and then choose the Display button.”`  
  
2. Jeśli TextBlock nie jest powiększony, aby dopasować widoku w projekcie, Powiększ formant TextBlock (za pomocą uchwytów na krawędziach) tak, aby wyświetlał cały tekst.  
  
3. Zapisz zmiany, naciskając klawisze Ctrl + s lub za pomocą **pliku** elementu menu.  
  
   Następnie należy dodać dwie [RadioButton](http://msdn.microsoft.com/library/6c9ba847-eab7-4bba-9c74-6b56ef72067b) formantów do formularza.  
  
##### <a name="to-add-radio-buttons"></a>Aby dodać przyciski radiowe  
  
1. W **przybornika**, wyszukaj formant RadioButton.  
  
    ![Okno przybornika z wybraniu kontrolki RadioButton](../ide/media/exploreide-radiobuttontoolbox.png "ExploreIDE RadioButtonToolbox")  
  
2. Dodaj dwa formanty RadioButton do projektowania, surface, wybierając element RadioButton i przeciągając je do okna na powierzchni projektowej dwa razy, a następnie przenieść przycisków (wybierając je, a za pomocą klawiszy strzałek) tak, aby przyciski są wyświetlane obok siebie w TextBlock formant.  
  
    Okno powinno wyglądać następująco:  
  
    Rysunek 8: Przyciski radiowe w oknie Greetings.  
  
    ![Pozdrowienia formularza z textblock oraz dwa przyciski radiowe](../ide/media/exploreide-greetingswithradiobuttons.png "ExploreIDE Greetingswithradiobuttons")  
  
3. W **właściwości** okna dla lewego formantu RadioButton, zmień **nazwa** właściwości (właściwość w górnej części **właściwości** okna) do `RadioButton1`.  Upewnij się, że wybrano RadioButton, a nie w tle siatce na formularzu. pole "Type" w oknie właściwości, w polu Nazwa powinna być widoczna nazwa RadioButton.  
  
4. W **właściwości** okna dla prawego formantu RadioButton, zmień **nazwa** właściwości `RadioButton2`, a następnie zapisz zmiany, naciskając klawisze Ctrl + s lub za pomocą **pliku**elementu menu.  Upewnij się, że wybrano RadioButton przed zmianę i zapisywanie.  
  
   Możesz teraz dodawać wyświetlany tekst dla każdego formantu RadioButton. Następująca procedura aktualizuje **zawartości** właściwości dla kontrolki RadioButton.  
  
##### <a name="to-add-display-text-for-each-radio-button"></a>Aby dodać wyświetlany tekst dla każdego przycisku radiowego  
  
1. Na powierzchni projektowej Otwórz menu skrótów dla RadioButton1, naciskając klawisz prawego przycisku myszy podczas wybierania RadioButton1, wybierz polecenie **Edycja tekstu**, a następnie wprowadź `Hello`.  
  
2. Otwórz menu skrótów dla RadioButton2, naciskając klawisz prawego przycisku myszy podczas wybierania RadioButton2, wybierz polecenie **Edycja tekstu**, a następnie wprowadź `Goodbye`.  
  
   Ostatnim elementem interfejsu użytkownika, jaki dodasz, jest [przycisk](http://msdn.microsoft.com/library/a9d8f5a5-c98c-463e-808a-5a4e63173098) kontroli.  
  
##### <a name="to-add-the-button-control"></a>Aby dodać kontrolkę przycisku  
  
1. W **przybornika**, wyszukaj **przycisk** sterowania, a następnie dodaj go do powierzchni projektowej, w obszarze formantów RadioButton, wybierając przycisk i przeciągając je do formularza w widoku Projekt.  
  
2. W widoku XAML, zmień wartość **zawartości** dla formantu Button z `Content=”Button”` do `Content=”Display”`, a następnie zapisz zmiany (Ctrl + s, lub użyj **pliku** menu).  
  
    Znaczniki powinny być podobne do następującego przykładu: `<Button Content="Display" HorizontalAlignment="Left" VerticalAlignment="Top" Width="75" Margin="215,204,0,0"/>`  
  
   Okno powinno wyglądać podobnie, jak na poniższej ilustracji.  
  
   Rysunek 9: Końcowy interfejs użytkownika Greetings  
  
   ![Pozdrowienia formularza z etykietami kontroli](../ide/media/exploreide-greetingswithconrollabels.png "ExploreIDE Greetingswithconrollabels")  
  
### <a name="add-code-to-the-display-button"></a>Dodaj kod do przycisku Display  
 Gdy aplikacja jest uruchomiona, okno komunikatu pojawia się po użytkownik najpierw wybierze przycisk radiowy, a następnie **wyświetlania** przycisku. Jedno okno komunikatu pojawi się, żeby wyświetlić „Hello”, a inne pojawi się, aby wyświetlić „Goodbye”. Aby uzyskać takie zachowanie, dodasz kod do zdarzenia Button_Click w Greetings.xaml.vb lub Greetings.xaml.cs.  
  
##### <a name="add-code-to-display-message-boxes"></a>Dodaj kod do wyświetlania okien komunikatów  
  
1. Na powierzchni projektowej kliknij dwukrotnie **wyświetlania** przycisku.  
  
     Greetings.xaml.vb lub Greetings.xaml.cs otworzy się, kursor będzie się znajdował w zdarzeniu Button_Click. Można również dodać obsługę zdarzeń kliknięcia w następujący sposób (jeśli wklejonego kodu ma czerwona fala dowolnej nazwy, należy prawdopodobnie nie wybrać formantów RadioButton na powierzchni projektowej i zmień ich nazwy):  
  
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
  
## <a name="BKMK_DebugTest"></a> Debugowanie i testowanie aplikacji  
 Następnie należy debugować aplikację, aby wyszukać błędy i przetestować, czy oba okna komunikatów wyświetlają się poprawnie. Poniższe instrukcje informujące, jak utworzyć i uruchomić debugera, ale później mogą odczytać [Kompilowanie aplikacji WPF (WPF)](http://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c) i [debugowanie WPF](../debugger/debugging-wpf.md) Aby uzyskać więcej informacji.  
  
### <a name="find-and-fix-errors"></a>Znajdowanie i naprawianie błędów  
 W tym kroku można znaleźć błędy spowodowane wcześniej przez zmianę nazwy okna głównego pliku XAML.  
  
##### <a name="to-start-debugging-and-find-the-error"></a>Aby rozpocząć debugowanie i znaleźć błąd  
  
1. Uruchom debuger, wybierając **debugowania**, następnie **Rozpocznij debugowanie**.  
  
    ![Rozpocznij debugowanie poleceń w menu Debugowanie](../ide/media/exploreide-startdebugging.png "ExploreIDE StartDebugging")  
  
    Pojawi się okno dialogowe, wskazując, że wystąpił IOException: Nie można zlokalizować zasobu 'mainwindow.xaml'.  
  
2. Wybierz **OK** przycisk, a następnie Przerwij debugowanie.  
  
    ![Zatrzymaj debugowanie poleceń w menu Debugowanie](../ide/media/exploreide-stopdebugging.png "ExploreIDE StopDebugging")  
  
   Zmieniliśmy nazwę Mainwindow.xaml na Greetings.xaml na początku tego przewodnika, ale kod nadal odwołuje się do pliku Mainwindow.xaml jako startowy identyfikator URI dla aplikacji, więc nie można uruchomić projektu.  
  
##### <a name="to-specify-greetingsxaml-as-the-startup-uri"></a>Aby określić Greetings.xaml jako startowy identyfikator URI  
  
1. W **Eksploratora rozwiązań**, otwórz plik App.xaml (w projekcie języka C#) lub Application.XAML (w projekcie języka Visual Basic) w widoku XAML (nie można otworzyć w widoku Projekt), przez wybranie pliku, a następnie naciskając klawisz Enter lub podwójnej precyzji klikając go.  
  
2. Zmiana `StartupUri="MainWindow.xaml"` do `StartupUri="Greetings.xaml"`, a następnie zapisz zmiany Ctrl + s.  
  
   Uruchom ponownie debuger (naciśnij klawisz F5). Powinieneś zobaczyć okno powitania aplikacji.  
  
### <a name="to-debug-with-breakpoints"></a>Aby debugować z punktami przerwania  
 Dodając kilka punktów przerwania, można przetestować kod podczas debugowania. Możesz dodać punkty przerwania, wybierając **debugowania** w menu głównym, a następnie **Przełącz punkt przerwania** lub klikając w lewy margines edytora obok wiersza kodu, na którym ma nastąpić przerwanie.  
  
##### <a name="to-add-breakpoints"></a>Aby dodać punkty przerwania  
  
1. Otwórz Greetings.xaml.vb lub Greetings.xaml.cs i zaznacz następujący wiersz: `MessageBox.Show("Hello.")`  
  
2. Dodaj punkt przerwania z menu, wybierając **debugowania**, następnie **Przełącz punkt przerwania**.  
  
     ![Przełącz punkt przerwania — polecenie w menu Debugowanie](../ide/media/exploreide-togglebreakpoint.png "togglebreakpoint — ExploreIDE")  
  
     Obok wiersza kodu na marginesie po lewej stronie okna edytora jest wyświetlane czerwone koło.  
  
3. Zaznacz następujący wiersz: `MessageBox.Show("Goodbye.")`.  
  
4. Naciśnij klawisz F9, aby dodać punkt przerwania, a następnie naciśnij klawisz F5, aby rozpocząć debugowanie.  
  
5. W **Greetings** oknie Wybierz **Hello** przycisk radiowy, a następnie wybierz **wyświetlania** przycisku.  
  
     Wiersz `MessageBox.Show("Hello.")` jest wyróżniony na żółto. W dolnej części IDE, zmiennych automatycznych, zmienne lokalne i obejrzyj są zadokowane razem po lewej stronie, a stos wywołań, punkty przerwania, polecenia, bezpośrednie i dane wyjściowe są zadokowane razem po prawej stronie.  
  
6. Na pasku menu wybierz **debugowania**, **Step Out**.  
  
     Aplikacja wznawia działanie i pojawia się okno komunikatu z napisem „Hello”.  
  
7. Wybierz **OK** przycisk w oknie komunikatu, aby je zamknąć.  
  
8. W **Greetings** oknie Wybierz **Goodbye** przycisk radiowy, a następnie wybierz **wyświetlania** przycisku.  
  
     Wiersz `MessageBox.Show("Goodbye.")` jest wyróżniony na żółto.  
  
9. Wciśnij klawisz F5, aby kontynuować debugowanie. Gdy pojawi się okno komunikatu, wybierz **OK** przycisk w oknie komunikatu, aby je zamknąć.  
  
10. Naciśnij klawisze SHIFT + F5 kluczy (naciśnij klawisz shift, najpierw i przytrzymując wciśnięty, naciśnij klawisz F5) aby zatrzymać debugowanie.  
  
11. Na pasku menu wybierz **debugowania**, **Wyłącz wszystkie punkty przerwania**.  
  
### <a name="build-a-release-version-of-the-application"></a>Tworzenie dystrybucyjnej wersji tej aplikacji  
 Teraz, gdy masz już pewność, że wszystko działa, możesz przygotować wersję dystrybucyjną aplikacji.  
  
##### <a name="to-clean-the-solution-files-and-build-a-release-version"></a>Aby wyczyścić pliki rozwiązań i zbudować wersję przeznaczoną do publikacji  
  
1. W menu głównym wybierz **kompilacji**, następnie **czyść rozwiązanie** można usunąć pliki pośrednie i pliki wyjściowe, które zostały utworzone podczas poprzednich kompilacji.  Nie jest to konieczne, ale go czyści dane wyjściowe z kompilacji debugowania.  
  
    ![Polecenie Wyczyść rozwiązanie, w menu kompilacja](../ide/media/exploreide-cleansolution.png "ExploreIDE CleanSolution")  
  
2. Zmień konfigurację kompilacji dla HelloWPFApp z **debugowania** do **wersji** za pomocą formantu listy rozwijanej na pasku narzędzi (wyświetlany jest tekst "Debugowanie" obecnie).  
  
    ![Standardowy pasek narzędzi w wersji wybrane](../ide/media/exploreide-releaseversion.png "ExploreIDE ReleaseVersion")  
  
3. Skompiluj rozwiązanie, wybierając **kompilacji**, następnie **Kompiluj rozwiązanie** lub naciśnij klawisz F6.  
  
    ![Kompiluj rozwiązanie, polecenie w menu kompilacja](../ide/media/exploreide-buildsolution.png "Skompiluj rozwiązanie ExploreIDE")  
  
   Gratulujemy zakończenia instruktażu! Możesz znaleźć .exe utworzone w katalogu rozwiązania i projektu (...\HelloWPFApp\HelloWPFApp\bin\Release\\). Jeśli chcesz poznać więcej przykładów, zobacz [Visual Studio Samples](../ide/visual-studio-samples.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Co nowego w programie Visual Studio 2015](../what-s-new-in-visual-studio-2015.md)   
 [Rozpocznij tworzenie aplikacji za pomocą programu Visual Studio](../ide/get-started-developing-with-visual-studio.md)   
 [Wskazówki dotyczące produktywności](../ide/productivity-tips-for-visual-studio.md)
