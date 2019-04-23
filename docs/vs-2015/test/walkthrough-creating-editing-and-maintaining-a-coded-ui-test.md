---
title: 'Przewodnik: Tworzenia, edytowania i utrzymywania kodowanego testu interfejsu użytkownika | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: f7c25ba7-5c9c-455b-9242-701cda56f90c
caps.latest.revision: 43
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8df705e1e4da6a54f060de45a90aed7c41691683
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60061817"
---
# <a name="walkthrough-creating-editing-and-maintaining-a-coded-ui-test"></a>Przewodnik: Tworzenia, edytowania i utrzymywania kodowanego testu interfejsu użytkownika
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podręcznik pozwala utworzyć prostą aplikację Windows Presentation Foundation (WPF) do przedstawienia sposobu tworzenia, edytowania i utrzymywania kodowanego testu interfejsu użytkownika. Dostarcza on rozwiązania do korekcji testów, które zostały uszkodzone przez różne problemy związane z czasem i refaktoryzacją kontroli.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Oprócz przewodnika potrzeba:  
  
- Visual Studio Enterprise  
  
### <a name="create-a-simple-wpf-application"></a>Tworzenie prostej aplikacji WPF  
  
1. Na **pliku** menu wskaż **New**, a następnie wybierz pozycję **projektu**.  
  
     **Nowy projekt** pojawi się okno dialogowe.  
  
2. W **zainstalowane** okienku rozwiń **Visual C#**, a następnie wybierz pozycję **pulpitu Windows**.  
  
3. Nad środkowym okienkiem Sprawdź, czy ma wartość listy rozwijanej target framework **.NET Framework 4.5**.  
  
4. W środkowym okienku wybierz **aplikacji WPF** szablonu.  
  
5. W **nazwa** polu tekstowym **SimpleWPFApp**.  
  
6. Wybierz folder, w którym zapiszesz projekt. W **lokalizacji** tekstu wpisz nazwę folderu.  
  
7. Wybierz **OK**.  
  
     Zostanie otwarty program The WPF Designer for Visual Studio i pojawi się główne okno projektu.  
  
8. Jeśli przybornik nie jest otwarty, otwórz go. Wybierz **WIDOKU** menu, a następnie wybierz **przybornika**.  
  
9. W obszarze **wszystkie formanty WPF** sekcji, przeciągnij **przycisk**, **wyboru** i **ProgressBar** projektową okna głównego w projekcie powierzchni.  
  
10. Zaznacz formant przycisku. W oknie Właściwości zmień wartość **nazwa** właściwość \<Brak nazwy > na button1. Następnie zmień wartość **zawartości** właściwość przycisk do ekranu startowego.  
  
11. Zaznacz formant paska postępu. W oknie Właściwości zmień wartość na wartość **nazwa** właściwość \<Brak nazwy > na progressBar1. Następnie zmień wartość **maksymalna** właściwość **100** do **10000**.  
  
12. Zaznacz formant pola wyboru. W oknie Właściwości zmień wartość **nazwa** właściwość \<Brak nazwy > na checkBox1 i wyczyść **IsEnabled** właściwości.  
  
     ![Simple WPF Application](../test/media/codedui-wpfapp.png "CodedUI_WPFApp")  
  
13. Kliknij dwukrotnie formant przycisku aby dodać obsługę zdarzeń kliknięcia.  
  
     MainWindow.xmal.cs jest wyświetlany w edytorze kodu, z kursorem w nowej metodzie button1_Click.  
  
14. W górnej części klasy MainWindow dodaj delegata. Delegat będzie używany dla paska postępu. Aby dodać delegata, dodaj następujący kod:  
  
    ```csharp  
    public partial class MainWindow : Window  
    {  
            private delegate void ProgressBarDelegate(System.Windows.DependencyProperty dp, Object value);          
  
        public MainWindow()  
        {  
  
            InitializeComponent();  
        }  
  
    ```  
  
15. W metodzie button1_Click dodaj następujący kod:  
  
    ```csharp  
    private void button1_Click(object sender, RoutedEventArgs e)  
    {  
        double progress = 0;  
  
        ProgressBarDelegate updatePbDelegate =  
            new ProgressBarDelegate(progressBar1.SetValue);  
  
        do  
        {  
            progress ++;  
  
            Dispatcher.Invoke(updatePbDelegate,  
                System.Windows.Threading.DispatcherPriority.Background,  
                new object[] { ProgressBar.ValueProperty, progress });  
            progressBar1.Value = progress;  
        }  
        while (progressBar1.Value != progressBar1.Maximum);  
  
        checkBox1.IsEnabled = true;  
    }  
  
    ```  
  
16. Zapisz plik.  
  
### <a name="verify-the-wpf-application-runs-correctly"></a>Weryfikowanie prawidłowego uruchamiania aplikacji WPF  
  
1. Na **debugowania** menu, wybierz opcję **Rozpocznij debugowanie** lub naciśnij **F5**.  
  
2. Należy zauważyć, że kontrolka pola wyboru jest wyłączona. Wybierz **Start**.  
  
     W ciągu kilku sekund pasek postępu powinien być zapełniony w 100%.  
  
3. Możesz teraz wybrać kontrolkę pola wyboru.  
  
4. Zamknij aplikację SimpleWPFApp.  
  
### <a name="create-and-run-a-coded-ui-test-for-simplewpfapp"></a>Tworzenie i uruchamianie kodowanego testu interfejsu użytkownika dla aplikacji SimpleWPFApp  
  
1. Znajdź aplikację SimpleWPFApp, która została utworzona wcześniej. Domyślnie aplikacja zostanie umieszczona w C:\Users\\< nazwa_użytkownika\>\Documents\Visual Studio \<wersji > \Projects\SimpleWPFApp\SimpleWPFApp\bin\Debug\SimpleWPFApp.exe  
  
2. Utwórz na pulpicie skrót do aplikacji SimpleWPFApp. Kliknij prawym przyciskiem myszy SimpleWPFApp.exe i wybierz polecenie **kopiowania**. Na pulpicie kliknij prawym przyciskiem myszy i wybierz polecenie **Wklej skrót**.  
  
    > [!TIP]
    >  Skrót do aplikacji ułatwia dodawanie lub modyfikowanie kodowanych testów interfejsu użytkownika dla aplikacji, ponieważ pozwala to na szybkie uruchamianie aplikacji.  
  
3. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy rozwiązanie, wybierz polecenie **Dodaj** , a następnie wybierz **nowy projekt**.  
  
     **Dodaj nowy projekt** pojawi się okno dialogowe.  
  
4. W **zainstalowane** okienku rozwiń **Visual C#**, a następnie wybierz pozycję **testu**.  
  
5. W środkowym okienku wybierz **projekt kodowanego testu interfejsu użytkownika** szablonu.  
  
6. Wybierz **OK**.  
  
     W Eksploratorze rozwiązań kliknij nowy kodowanego testu interfejsu użytkownika o nazwie **CodedUITestProject1** jest dodawany do rozwiązania.  
  
     **Generuj kod dla kodowanego testu interfejsu użytkownika** pojawi się okno dialogowe.  
  
7. Wybierz **Rejestruj akcje, Edytuj mapę interfejsu użytkownika lub Dodaj potwierdzenia** opcji, a następnie wybierz **OK**.  
  
     Uimap — Konstruktor kodowanego testu interfejsu użytkownika w pojawia się i jest zminimalizowane okno programu Visual Studio.  
  
     Aby uzyskać więcej informacji na temat opcji w oknie dialogowym, zobacz [tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).  
  
8. Wybierz **Rozpocznij nagrywanie** w uimap — Konstruktor kodowanego testu interfejsu użytkownika.  
  
     ![Rozpocznij nagrywanie](../test/media/cuit-builder-record.png "CUIT_Builder_Record")  
  
     Można zatrzymać nagrywanie, jeśli to konieczne, na przykład jeśli masz do czynienia z przychodzących wiadomości e-mail.  
  
     ![Wstrzymanie nagrywania](../test/media/cuit.png "CUIT_")  
  
    > [!WARNING]
    >  Wszystkie akcje wykonywane na pulpicie będą rejestrowane. Wstrzymanie nagrywania, jeśli są wykonywane działania, które mogą prowadzić do danych poufnych jest zawarty w nagraniu.  
  
9. Uruchamianie aplikacji za pomocą skrótu na pulpicie.  
  
     Tak jak poprzednio Zwróć uwagę, że kontrolka pola wyboru jest wyłączona.  
  
10. W aplikacji, wybierz **Start**.  
  
     W ciągu kilku sekund pasek postępu powinien być zapełniony w 100%.  
  
11. Zaznacz formant pola wyboru, która jest teraz włączony.  
  
12. Zamknij aplikację SimpleWPFApp.  
  
13. W UIMap — Konstruktor kodowanego testu interfejsu użytkownika, wybierz **Generuj kod**.  
  
14. W polu wpisz nazwę metody **SimpleAppTest** i wybierz polecenie **Dodaj i Generuj**. W ciągu kilku sekund Kodowany test interfejsu użytkownika pojawi się i będzie dodany do rozwiązania.  
  
15. Zamknij UIMap — Konstruktor kodowanego testu interfejsu użytkownika.  
  
     Plik CodedUITest1.cs pojawi się w edytorze kodu.  
  
16. Zapisz projekt.  
  
### <a name="run-the-coded-ui-test"></a>Uruchamianie kodowanego testu interfejsu użytkownika.  
  
1. Z **testu** menu, wybierz **Windows** , a następnie wybierz **Eksplorator testów**.  
  
2. Z **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.  
  
3. W pliku CodedUITest1.cs zlokalizuj **CodedUITestMethod** , kliknij prawym przyciskiem myszy i wybierz opcję **Uruchom testy**, lub uruchamiać testy z Eksploratora testów.  
  
     Podczas wykonywania kodowanego przebiegu testu interfejsu użytkownika aplikacja SimpleWPFApp jest widoczna. Wykonuje ona działania, których nie było w poprzedniej procedurze. Jednak gdy test próbuje zaznaczyć pole wyboru, formantu pola wyboru, w oknie wyników pokazuje, że test nie powiódł się. Ponieważ test próbuje zaznaczyć pole wyboru, ale nie ma informacji, że kontrolka pola wyboru jest wyłączona, dopóki pasek postępu nie zostanie zapełniony w 100%. Możesz rozwiązać ten i podobne problemy za pomocą różnych `UITestControl.WaitForControlXXX()` metod, które są dostępne dla kodowanego testowania interfejsu użytkownika. Następna procedura wykaże za pomocą `WaitForControlEnabled()` metodę, aby rozwiązać ten problem, który spowodował niepowodzenie testu. Aby uzyskać więcej informacji, zobacz [wprowadzania kodowanego interfejsu użytkownika testy oczekiwania dla określonych zdarzeń podczas odtwarzania](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md).  
  
### <a name="edit-and-rerun-the-coded-ui-test"></a>Edytowanie i ponowne uruchamianie kodowanego testu interfejsu użytkownika  
  
1. W oknie Eksploratora testów zaznacz test zakończony niepowodzeniem i **ślad stosu** sekcji, wybierz pierwsze łącze do **UIMap.SimpleAppTest()**.  
  
2. Plik UIMap.Designer.cs otwiera się z punktem błędu wyróżnionego w kodzie:  
  
    ```csharp  
  
    // Select 'CheckBox' check box  
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;  
    ```  
  
3. Aby rozwiązać ten problem, może wykonać kodowany test interfejsu użytkownika, poczekaj, aż formant CheckBox zostanie włączony przed przejściem do tego wiersza przy użyciu `WaitForControlEnabled()` metody.  
  
    > [!WARNING]
    >  Nie należy modyfikować pliku UIMap.Designer.cs. Wszelkie zmiany kodu wprowadzone w pliku UIMapDesigner.cs zostaną każdorazowo zastąpione przy generowaniu kodu za pomocą UIMap — Konstruktora kodowanego testu interfejsu użytkownika. Jeśli trzeba zmodyfikować nagraną metodę, należy skopiować ją do pliku UIMap.cs i zmienić jej nazwę. Plik UIMap.cs może służyć do zastępowania metod i właściwości w pliku UIMapDesigner.cs. Musisz usunąć odwołanie do oryginalnej metody w pliku Coded UITest.cs, a następnie zastąpić je zmienioną nazwą metody.  
  
4. W Eksploratorze rozwiązań zlokalizuj **UIMap.uitest** w projekt kodowanego testu interfejsu użytkownika.  
  
5. Otwórz menu skrótów dla **UIMap.uitest** i wybierz polecenie **Otwórz**.  
  
     Kodowany test interfejsu użytkownika jest wyświetlany w Edytorze kodowanego testu interfejsu użytkownika. Teraz można wyświetlać i edytować kodowany test interfejsu użytkownika.  
  
6. W **działania interfejsu użytkownika** okienku, wybierz metodę testową (SimpleAppTest), która ma zostać przeniesiony do pliku UIMap.cs lub UIMap.vb w celu ułatwienia działania kodu niestandardowego, który nie zostanie zastąpiony po kod testu jest ponownie kompilowana.  
  
7. Wybierz **Przenieś kod** przycisk na pasku narzędzi edytora kodowanego testu interfejsu użytkownika.  
  
8. Pojawi się okno dialogowe programu Microsoft Visual Studio. Zawiera ono ostrzeżenie, że metoda ta ma zostać przeniesiona z pliku UIMap.uitest do pliku UIMap.cs i nie będzie już można edytować metody za pomocą Edytora kodowanego testu interfejsu użytkownika. Wybierz **tak**.  
  
     Metoda testu jest usuwana z pliku UIMap.uitest i nie jest już wyświetlana w okienku Akcje interfejsu użytkownika. Aby edytować przeniesiony plik testowy, otwórz plik UIMap.cs w Eksploratorze rozwiązań.  
  
9. Na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] narzędzi, wybierz **Zapisz**.  
  
     Aktualizacje do metody testowej są zapisywane w pliku UIMap.Designer.  
  
    > [!CAUTION]
    >  Po przeniesieniu metody nie będzie można edytować jej za pomocą Edytora kodowanego testu interfejsu użytkownika. Należy dodać niestandardowy kod i obsługiwać go za pomocą Edytora kodu.  
  
10. Zmień nazwę metody z `SimpleAppTest()` do `ModifiedSimpleAppTest()`  
  
11. Dodaj następującą instrukcję using do pliku:  
  
    ```csharp  
  
    using Microsoft.VisualStudio.TestTools.UITesting.WpfControls;  
  
    ```  
  
12. Dodaj następujący kod `WaitForControlEnabled()` metoda przed naruszającym wierszem kodu zidentyfikowanym wcześniej:  
  
    ```csharp  
  
              uICheckBoxCheckBox.WaitForControlEnabled();  
  
    // Select 'CheckBox' check box  
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;  
  
    ```  
  
13. W pliku CodedUITest1.cs zlokalizuj **CodedUITestMethod** metody, a następnie przekształcić w komentarz lub zmień nazwę odniesienia do oryginalnej metody SimpleAppTest() i Zastąp nowym testem ModifiedSimpleAppTest():  
  
    ```csharp  
    [TestMethod]  
            public void CodedUITestMethod1()  
            {  
                // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.  
                // For more information on generated code, see http://go.microsoft.com/fwlink/?LinkId=179463  
                //this.UIMap.SimpleAppTest();  
                this.UIMap.ModifiedSimpleAppTest();  
            }  
  
    ```  
  
14. Na **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.  
  
15. Kliknij prawym przyciskiem myszy **CodedUITestMethod** i wybierz opcję **Uruchom testy**.  
  
16. Tym razem kodowany test interfejsu użytkownika pomyślnie zakończy wszystkie etapy testu i **zakończone powodzeniem** są wyświetlane w oknie Eksploratora testów.  
  
### <a name="refactor-a-control-in-the-simplewpfapp"></a>Reorganizacja formantu w aplikacji SimpleWPFApp  
  
1. W pliku MainWindow.xaml w Projektancie zaznacz formant przycisku.  
  
2. W górnej części w oknie Właściwości zmień **nazwa** wartości właściwości z button1 na buttonA.  
  
3. Na **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.  
  
4. W Eksploratorze testów, uruchom **CodedUITestMethod1**.  
  
     Test zakończy się niepowodzeniem, ponieważ w UIMap jako button1 kodowany test interfejsu użytkownika nie można znaleźć formantu przycisku, który pierwotnie był mapowany. Refaktoryzacja może w ten sposób wpłynąć na kodowane testy interfejsu użytkownika.  
  
5. W oknie Eksploratora testów w **ślad stosu** sekcji, wybierz pierwsze łącze obok **(UIMpa.ModifiedSimpleAppTest)**.  
  
     Zostanie otwarty plik UIMap.cs. Punkt błędu jest wyróżniany w kodzie:  
  
    ```csharp  
  
    // Click 'Start' button  
    Mouse.Click(uIStartButton, new Point(27, 10));  
    ```  
  
     Należy zauważyć, że w wierszu kodu wcześniej w tej procedurze jest przy użyciu `UiStartButton`, która była nazwą UIMap, zanim został wycofany.  
  
     Aby rozwiązać ten problem, można dodać wycofany formant do UIMap za pomocą Konstruktora kodowanego testu interfejsu użytkownika. Można zaktualizować kod testu do użycia kodu, jak przedstawiono w następnej procedurze.  
  
### <a name="map-refactored-control-and-edit-and-rerun-the-coded-ui-test"></a>Mapowanie wycofanej kontroli i edycji oraz ponowne przeprowadzenie kodowanego testu interfejsu użytkownika  
  
1. W pliku CodedUITest1.cs w **CodedUITestMethod1()** metody, kliknij prawym przyciskiem myszy, wybierz opcję **Generuj kod dla kodowanego testu interfejsu użytkownika** , a następnie wybierz **Użyj kodowanego testu interfejsu użytkownika**.  
  
     Pojawi się UIMap — Konstruktor kodowanego testu interfejsu użytkownika.  
  
2. Przy użyciu utworzonego wcześniej skrótu na pulpicie, uruchom aplikację SimpleWPFApp, która została utworzona wcześniej.  
  
3. W uimap — Konstruktor kodowanego testu interfejsu użytkownika, przeciągnij narzędzie krzyżyka do **Start** przycisku w aplikacji.  
  
     **Start** przycisk jest ujęty w niebieskie pole, a Konstruktor kodowanego testu interfejsu użytkownika zajmuje kilka sekund do przetwarzania danych dla wybranej kontrolki i wyświetlenie właściwości formantów. Należy zauważyć, że **AutomationUId** nosi nazwę **buttonA**.  
  
4. We właściwościach formantu wybierz strzałkę w lewym górnym rogu, aby rozwinąć Mapę formantów UI. Należy zauważyć, że **UIStartButton1** jest zaznaczone.  
  
5. Na pasku narzędzi wybierz **dodać formant do mapy formantów UI**.  
  
     Stan w dolnej części okna sprawdza akcję poprzez wyświetlenie **zaznaczony formant został dodany do mapy formantów UI**.  
  
6. W uimap — Konstruktor kodowanego testu interfejsu użytkownika, wybierz **Generuj kod**.  
  
     Konstruktor testu kodowanego interfejsu użytkownika — Generuj kod pojawia się z uwagą wskazującą, że nie jest wymagana żadna nowa metoda, a kod zostanie wygenerowany wyłącznie dla zmian w mapie formantów interfejsu użytkownika.  
  
7. Wybierz **Generowanie**.  
  
8. Zamknij aplikację SimpleWPFApp.exe.  
  
9. Zamknij UIMap — Konstruktor kodowanego testu interfejsu użytkownika.  
  
     UIMap — Konstruktor kodowanego testu interfejsu użytkownika potrzebuje kilku sekund, aby przetworzyć zmiany mapy formantów interfejsu użytkownika.  
  
10. W Eksploratorze rozwiązań otwórz plik UIMap.Designer.cs.  
  
11. W pliku UIMap.Designer.cs zlokalizować właściwości UIStartButton1. Zwróć uwagę `SearchProperties` ustawiono `"buttonA"`:  
  
    ```csharp  
  
    public WpfButton UIStartButton1  
            {  
                get  
                {  
                    if ((this.mUIStartButton1 == null))  
                    {  
                        this.mUIStartButton1 = new WpfButton(this);  
                        #region Search Criteria  
                        this.mUIStartButton1.SearchProperties[WpfButton.PropertyNames.AutomationId] = "buttonA";  
                        this.mUIStartButton1.WindowTitles.Add("MainWindow");  
                        #endregion  
                    }  
                    return this.mUIStartButton1;  
                }  
            }  
  
    ```  
  
     Teraz można zmodyfikować kodowany test interfejsu użytkownika do korzystania z ostatnio mapowanego formantu. Jak wskazano w poprzedniej procedurze, aby zastąpić jakąkolwiek metodę lub właściwości w kodowanym teście interfejsu użytkownika, należy to zrobić w pliku UIMap.cs.  
  
12. W pliku UIMap.cs Dodaj konstruktora i określ `SearchProperties` właściwość `UIStartButton` właściwości, aby korzystała `AutomationID` właściwość z wartością `"buttonA":`  
  
    ```csharp  
  
    public UIMap()  
            {  
                this.UIMainWindowWindow.UIStartButton.SearchProperties[WpfButton.PropertyNames.AutomationId] = "buttonA";  
            }  
  
    ```  
  
13. Na **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.  
  
14. W Eksploratorze testów Uruchom okno CodedUITestMethod1.  
  
     Tym razem kodowany test interfejsu użytkownika pomyślnie zakończy wszystkie etapy testu.  W oknie wyników testu zostanie wyświetlony stan **zakończone powodzeniem**.  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
  
### <a name="videos"></a>Wideo  
 ![Link do wideo](../data-tools/media/playvideo.gif "PlayVideo") [kodowanego interfejsu użytkownika testów-DeepDive-Episode1-GettingStarted](http://go.microsoft.com/fwlink/?LinkID=230573)  
  
 ![Link do wideo](../data-tools/media/playvideo.gif "PlayVideo") [kodowanego interfejsu użytkownika testów-DeepDive-Episode2-MaintainenceAndDebugging](http://go.microsoft.com/fwlink/?LinkID=230574)  
  
 ![Link do wideo](../data-tools/media/playvideo.gif "PlayVideo") [kodowanego interfejsu użytkownika testów-DeepDive-Episode3-HandCoding](http://go.microsoft.com/fwlink/?LinkID=230575)  
  
### <a name="hands-on-lab"></a>Ćwiczenia praktyczne  
 [MSDN Virtual Lab: Wprowadzenie do tworzenia kodowanych testów interfejsu użytkownika w programie Visual Studio 2010](http://go.microsoft.com/fwlink/?LinkID=22508)  
  
### <a name="faq"></a>Najczęściej zadawane pytania  
 [Kodowane testy interfejsu użytkownika — często zadawane pytania — 1](http://go.microsoft.com/fwlink/?LinkID=230576)  
  
 [Kodowanych testów interfejsu użytkownika — często zadawane pytania -2](http://go.microsoft.com/fwlink/?LinkID=230578)  
  
### <a name="forum"></a>Forum  
 [Visual Studio automatyczne testowanie interfejsu użytkownika (w tym CodedUI)](http://go.microsoft.com/fwlink/?LinkID=224497)  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)   
 [Wprowadzenie do projektanta WPF](http://msdn.microsoft.com/18e61d03-b96a-4058-a166-8ec6b3f6116b)   
 [Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i nagrywania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)   
 [Edytowanie kodowanych testów interfejsu użytkownika za pomocą edytora kodowanych testów interfejsu użytkownika](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)
