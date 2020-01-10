---
title: 'Przewodnik: Tworzenie, edytowanie i obsługa kodowanego testu interfejsu użytkownika | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: f7c25ba7-5c9c-455b-9242-701cda56f90c
caps.latest.revision: 43
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d14de396e24874f39a09172a483ebef81a5886f2
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851231"
---
# <a name="walkthrough-creating-editing-and-maintaining-a-coded-ui-test"></a>Wskazówki: tworzenie, edytowanie i obsługa kodowanego testu interfejsu użytkownika
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podręcznik pozwala utworzyć prostą aplikację Windows Presentation Foundation (WPF) do przedstawienia sposobu tworzenia, edytowania i utrzymywania kodowanego testu interfejsu użytkownika. Dostarcza on rozwiązania do korekcji testów, które zostały uszkodzone przez różne problemy związane z czasem i refaktoryzacją kontroli.

## <a name="prerequisites"></a>Wymagania wstępne
 Oprócz przewodnika potrzeba:

- Visual Studio Enterprise

### <a name="create-a-simple-wpf-application"></a>Tworzenie prostej aplikacji WPF

1. W menu **plik** wskaż polecenie **Nowy**, a następnie wybierz pozycję **projekt**.

     **Nowy projekt** pojawi się okno dialogowe.

2. W okienku **zainstalowane** rozwiń pozycję **Wizualizacja C#** , a następnie wybierz pozycję **pulpit systemu Windows**.

3. W środkowym okienku Sprawdź, czy na liście rozwijanej platformy docelowej jest ustawiona wartość **.NET Framework 4,5**.

4. W środkowym okienku wybierz szablon **Aplikacja WPF** .

5. W polu tekstowym **Nazwa** wpisz **SimpleWPFApp**.

6. Wybierz folder, w którym zapiszesz projekt. W polu tekstowym **Lokalizacja** wpisz nazwę folderu.

7. Wybierz **OK**.

     Zostanie otwarty program The WPF Designer for Visual Studio i pojawi się główne okno projektu.

8. Jeśli przybornik nie jest otwarty, otwórz go. Wybierz menu **Widok** , a następnie wybierz **Przybornik**.

9. W sekcji **wszystkie kontrolki WPF** przeciągnij **przycisk**, **pole wyboru** i formant **ProgressBar** na MainWindow na powierzchni projektowej.

10. Zaznacz formant przycisku. W okno Właściwości zmień wartość właściwości **Nazwa** z \<brak nazwy > na Button1. Następnie zmień wartość właściwości **zawartość** z przycisku na Rozpocznij.

11. Zaznacz formant paska postępu. W okno Właściwości zmień wartość właściwości **Nazwa** z \<brak nazwy > na ProgressBar1. Następnie zmień wartość właściwości **Maximum** z **100** na **10000**.

12. Zaznacz formant pola wyboru. W okno Właściwości zmień wartość właściwości **Nazwa** z \<brak nazwy > na checkBox1 i wyczyść Właściwość **IsEnabled** .

     ![Prosta aplikacja WPF](../test/media/codedui-wpfapp.png "CodedUI_WPFApp")

13. Kliknij dwukrotnie formant przycisku, aby dodać program obsługi zdarzeń kliknięcia.

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

1. W menu **Debuguj** wybierz polecenie **Rozpocznij debugowanie** lub naciśnij klawisz **F5**.

2. Zauważ, że formant pola wyboru jest wyłączony. Wybierz pozycję **Rozpocznij**.

     W ciągu kilku sekund pasek postępu powinien być zapełniony w 100%.

3. Teraz możesz wybrać kontrolkę pole wyboru.

4. Zamknij aplikację SimpleWPFApp.

### <a name="create-and-run-a-coded-ui-test-for-simplewpfapp"></a>Tworzenie i uruchamianie kodowanego testu interfejsu użytkownika dla aplikacji SimpleWPFApp

1. Znajdź utworzoną wcześniej aplikację SimpleWPFApp. Domyślnie aplikacja zostanie umieszczona w witrynie C:\Users\\< username\>\Documents\Visual Studio \<wersja > \Projects\SimpleWPFApp\SimpleWPFApp\bin\Debug\SimpleWPFApp.exe

2. Utwórz na pulpicie skrót do aplikacji SimpleWPFApp. Kliknij prawym przyciskiem myszy plik SimpleWPFApp. exe i wybierz polecenie **Kopiuj**. Na pulpicie kliknij prawym przyciskiem myszy i wybierz polecenie **Wklej skrót**.

    > [!TIP]
    > Skrót do aplikacji ułatwia dodawanie lub modyfikowanie kodowanych testów interfejsu użytkownika dla aplikacji, ponieważ pozwala to na szybkie uruchamianie aplikacji.

3. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy rozwiązanie, wybierz polecenie **Dodaj** , a następnie wybierz pozycję **Nowy projekt**.

     Pojawi się okno dialogowe **Dodaj nowy projekt** .

4. W okienku **zainstalowane** rozwiń pozycję **Wizualizacja C#** , a następnie wybierz pozycję **Testuj**.

5. W środkowym okienku wybierz szablon **projektu kodowanego testu interfejsu użytkownika** .

6. Wybierz **OK**.

     W Eksplorator rozwiązań nowy projekt kodowanego testu interfejsu użytkownika o nazwie **CodedUITestProject1** jest dodawany do rozwiązania.

     Zostanie wyświetlone okno dialogowe **generowanie kodu dla kodowanego testu interfejsu użytkownika** .

7. Wybierz opcję **Rejestruj akcje, Edytuj mapę interfejsu użytkownika lub Dodaj potwierdzenia** , a następnie wybierz **przycisk OK**.

     Pojawi się UIMap — Konstruktor kodowanego testu interfejsu użytkownika, a okno programu Visual Studio jest zminimalizowane.

     Aby uzyskać więcej informacji na temat opcji w oknie dialogowym, zobacz [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).

8. Wybierz pozycję **Rozpocznij nagrywanie** na UIMap — Konstruktor kodowanego testu interfejsu użytkownika.

     ![Rozpocznij nagrywanie](../test/media/cuit-builder-record.png "CUIT_Builder_Record")

     Możesz wstrzymać nagrywanie, jeśli jest to konieczne, na przykład w przypadku konieczności zajmowania się pocztą przychodzącą.

     ![Wstrzymaj nagrywanie](../test/media/cuit.png "CUIT_")

    > [!WARNING]
    > Wszystkie akcje wykonywane na pulpicie zostaną zarejestrowane. Wstrzymaj nagrywanie, jeśli wykonujesz akcje, które mogą prowadzić do zarejestrowania poufnych danych.

9. Uruchom SimpleWPFApp, używając skrótu na pulpicie.

     Tak jak wcześniej, Zauważ, że formant pola wyboru jest wyłączony.

10. Na SimpleWPFApp wybierz pozycję **Rozpocznij**.

     W ciągu kilku sekund pasek postępu powinien być zapełniony w 100%.

11. Zaznacz kontrolkę pole wyboru, która jest teraz włączona.

12. Zamknij aplikację SimpleWPFApp.

13. Na UIMap — Konstruktor kodowanego testu interfejsu użytkownika wybierz polecenie **Generuj kod**.

14. W polu Nazwa metody wpisz **SimpleAppTest** i wybierz polecenie **Dodaj i Generuj**. W ciągu kilku sekund Kodowany test interfejsu użytkownika pojawi się i będzie dodany do rozwiązania.

15. Zamknij UIMap — Konstruktor kodowanego testu interfejsu użytkownika.

     Plik CodedUITest1.cs pojawi się w edytorze kodu.

16. Zapisz projekt.

### <a name="run-the-coded-ui-test"></a>Uruchamianie kodowanego testu interfejsu użytkownika.

1. Z menu **test** wybierz pozycję **Windows** , a następnie wybierz **Eksplorator testów**.

2. Z menu **kompilacja** wybierz polecenie **Kompiluj rozwiązanie**.

3. W pliku CodedUITest1.cs Znajdź metodę **metodę CodedUITestMethod** , kliknij prawym przyciskiem myszy i wybierz polecenie **Uruchom testy**lub Uruchom test z Eksploratora testów.

     Podczas wykonywania kodowanego przebiegu testu interfejsu użytkownika aplikacja SimpleWPFApp jest widoczna. Wykonuje ona działania, których nie było w poprzedniej procedurze. Jednak gdy test próbuje zaznaczyć pole wyboru dla kontrolki pole wyboru, okno Wyniki testów pokazuje, że test zakończył się niepowodzeniem. Jest to spowodowane tym, że test próbuje zaznaczyć pole wyboru, ale nie wie, że formant pola wyboru jest wyłączony, dopóki pasek postępu nie zostanie ukończony do 100%. Te i podobne problemy można rozwiązać, korzystając z różnych `UITestControl.WaitForControlXXX()` metod, które są dostępne dla kodowanego testowania interfejsu użytkownika. Kolejna procedura przedstawia użycie metody `WaitForControlEnabled()` w celu rozwiązania problemu, który spowodował niepowodzenie tego testu. Aby uzyskać więcej informacji, zobacz [Tworzenie kodowanych testów interfejsu użytkownika w przypadku określonych zdarzeń podczas odtwarzania](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md).

### <a name="edit-and-rerun-the-coded-ui-test"></a>Edytowanie i ponowne uruchamianie kodowanego testu interfejsu użytkownika

1. W oknie Eksplorator testów wybierz test zakończony niepowodzeniem i w sekcji **ślad stosu** wybierz pierwszy link do **UIMap. SimpleAppTest ()** .

2. Plik UIMap.Designer.cs otwiera się z punktem błędu wyróżnionego w kodzie:

    ```csharp

    // Select 'CheckBox' check box
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;
    ```

3. Aby rozwiązać ten problem, można wykonać kodowane testy interfejsu użytkownika, aby zaczekać na włączenie kontrolki CheckBox przed kontynuowaniem tego wiersza przy użyciu metody `WaitForControlEnabled()`.

    > [!WARNING]
    > Nie należy modyfikować pliku UIMap.Designer.cs. Wszelkie zmiany kodu wprowadzone w pliku UIMapDesigner.cs zostaną każdorazowo zastąpione przy generowaniu kodu za pomocą UIMap — Konstruktora kodowanego testu interfejsu użytkownika. Jeśli trzeba zmodyfikować nagraną metodę, należy skopiować ją do pliku UIMap.cs i zmienić jej nazwę. Plik UIMap.cs może służyć do zastępowania metod i właściwości w pliku UIMapDesigner.cs. Musisz usunąć odwołanie do oryginalnej metody w pliku Coded UITest.cs, a następnie zastąpić je zmienioną nazwą metody.

4. W Eksplorator rozwiązań Zlokalizuj **UIMap. UITest** w projekcie kodowanego testu interfejsu użytkownika.

5. Otwórz menu skrótów dla **UIMap. UITest** i wybierz polecenie **Otwórz**.

     Kodowany test interfejsu użytkownika jest wyświetlany w Edytorze kodowanego testu interfejsu użytkownika. Teraz można wyświetlać i edytować kodowany test interfejsu użytkownika.

6. W okienku **Akcja interfejsu użytkownika** wybierz metodę testową (SimpleAppTest), która ma zostać przeniesiona do pliku UIMap.cs lub UIMap. vb, aby ułatwić niestandardowe funkcje kodu, które nie zostaną zastąpione podczas ponownej kompilacji kodu testowego.

7. Wybierz przycisk **Przenieś kod** na pasku narzędzi edytora kodowanego testu interfejsu użytkownika.

8. Pojawi się okno dialogowe programu Microsoft Visual Studio. Zawiera ono ostrzeżenie, że metoda ta ma zostać przeniesiona z pliku UIMap.uitest do pliku UIMap.cs i nie będzie już można edytować metody za pomocą Edytora kodowanego testu interfejsu użytkownika. Wybierz **tak**.

     Metoda testu jest usuwana z pliku UIMap.uitest i nie jest już wyświetlana w okienku Akcje interfejsu użytkownika. Aby edytować przeniesiony plik testowy, otwórz plik UIMap.cs w Eksploratorze rozwiązań.

9. Na pasku narzędzi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wybierz pozycję **Zapisz**.

     Aktualizacje do metody testowej są zapisywane w pliku UIMap.Designer.

    > [!CAUTION]
    > Po przeniesieniu metody nie będzie można edytować jej za pomocą Edytora kodowanego testu interfejsu użytkownika. Należy dodać niestandardowy kod i obsługiwać go za pomocą Edytora kodu.

10. Zmień nazwę metody z `SimpleAppTest()` na `ModifiedSimpleAppTest()`

11. Dodaj następującą instrukcję using do pliku:

    ```csharp

    using Microsoft.VisualStudio.TestTools.UITesting.WpfControls;

    ```

12. Dodaj następującą `WaitForControlEnabled()` metodę przed pokrytym wcześniej wierszem kodu:

    ```csharp

              uICheckBoxCheckBox.WaitForControlEnabled();

    // Select 'CheckBox' check box
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;

    ```

13. W pliku CodedUITest1.cs Znajdź metodę **metodę CodedUITestMethod** i Dodaj komentarz lub Zmień nazwę odwołania na oryginalną metodę SimpleAppTest (), a następnie zastąp ją nowym ModifiedSimpleAppTest ():

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

14. W menu **kompilacja** wybierz polecenie **Kompiluj rozwiązanie**.

15. Kliknij prawym przyciskiem myszy metodę **metodę CodedUITestMethod** i wybierz polecenie **Uruchom testy**.

16. Tym razem kodowany test interfejsu użytkownika pomyślnie zakończy wszystkie kroki testu, a w oknie Eksplorator testów zostanie wyświetlony komunikat **zakończony powodzeniem** .

### <a name="refactor-a-control-in-the-simplewpfapp"></a>Reorganizacja formantu w aplikacji SimpleWPFApp

1. W pliku MainWindow.xaml w Projektancie zaznacz formant przycisku.

2. W górnej części okno Właściwości zmień wartość właściwości **Nazwa** z Button1 na Button.

3. W menu **kompilacja** wybierz polecenie **Kompiluj rozwiązanie**.

4. W Eksploratorze testów Uruchom **okno CodedUITestMethod1**.

     Test zakończy się niepowodzeniem, ponieważ w UIMap jako button1 kodowany test interfejsu użytkownika nie można znaleźć formantu przycisku, który pierwotnie był mapowany. Refaktoryzacja może w ten sposób wpłynąć na kodowane testy interfejsu użytkownika.

5. W oknie Eksplorator testów w sekcji **ślad stosu** wybierz pierwszy link obok pozycji **UIMpa. ModifiedSimpleAppTest ()** .

     Zostanie otwarty plik UIMap.cs. Punkt błędu jest wyróżniany w kodzie:

    ```csharp

    // Click 'Start' button
    Mouse.Click(uIStartButton, new Point(27, 10));
    ```

     Należy zauważyć, że wiersz kodu we wcześniejszej części tej procedury używa `UiStartButton`, czyli nazwy UIMap przed przeprowadzeniem jej refaktoryzacji.

     Aby rozwiązać ten problem, można dodać wycofany formant do UIMap za pomocą Konstruktora kodowanego testu interfejsu użytkownika. Można zaktualizować kod testu do użycia kodu, jak przedstawiono w następnej procedurze.

### <a name="map-refactored-control-and-edit-and-rerun-the-coded-ui-test"></a>Mapowanie wycofanej kontroli i edycji oraz ponowne przeprowadzenie kodowanego testu interfejsu użytkownika

1. W pliku CodedUITest1.cs, w metodzie **okno CodedUITestMethod1 ()** , kliknij prawym przyciskiem myszy pozycję **Generuj kod dla KODOWANEGO testu interfejsu użytkownika** , a następnie wybierz opcję **Użyj konstruktora kodowanego testu interfejsu użytkownika**.

     Pojawi się UIMap — Konstruktor kodowanego testu interfejsu użytkownika.

2. Korzystając ze utworzonego wcześniej skrótu pulpitu, uruchom utworzoną wcześniej aplikację SimpleWPFApp.

3. W UIMap — Konstruktor kodowanego testu interfejsu użytkownika Przeciągnij narzędzie krzyżyka do przycisku **Start** na SimpleWPFApp.

     Przycisk **Start** znajduje się w niebieskim polu, a Konstruktor kodowanego testu interfejsu użytkownika zajmuje kilka sekund, aby przetworzyć dane dla wybranej kontrolki i wyświetlić właściwości kontrolek. Zwróć uwagę, że **AutomationUId** ma nazwę **Button**.

4. We właściwościach formantu wybierz strzałkę w lewym górnym rogu, aby rozwinąć Mapę formantów UI. Zauważ, że wybrano **UIStartButton1** .

5. Na pasku narzędzi wybierz **mapę Dodaj formant do kontrolki interfejsu użytkownika**.

     Stan u dołu okna weryfikuje akcję, wyświetlając **wybrany formant został dodany do mapy formantów interfejsu użytkownika**.

6. W UIMap — Konstruktor kodowanego testu interfejsu użytkownika wybierz polecenie **Generuj kod**.

     Konstruktor testu kodowanego interfejsu użytkownika — Generuj kod pojawia się z uwagą wskazującą, że nie jest wymagana żadna nowa metoda, a kod zostanie wygenerowany wyłącznie dla zmian w mapie formantów interfejsu użytkownika.

7. Wybierz pozycję **Generuj**.

8. Zamknij aplikację SimpleWPFApp.exe.

9. Zamknij UIMap — Konstruktor kodowanego testu interfejsu użytkownika.

     UIMap — Konstruktor kodowanego testu interfejsu użytkownika potrzebuje kilku sekund, aby przetworzyć zmiany mapy formantów interfejsu użytkownika.

10. W Eksploratorze rozwiązań otwórz plik UIMap.Designer.cs.

11. W pliku UIMap.Designer.cs Znajdź Właściwość UIStartButton1. Zauważ, że `SearchProperties` jest ustawiona na `"buttonA"`:

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

12. W pliku UIMap.cs Dodaj konstruktora i określ Właściwość `SearchProperties` właściwości `UIStartButton`, aby użyć właściwości `AutomationID` z wartością `"buttonA":`

    ```csharp

    public UIMap()
            {
                this.UIMainWindowWindow.UIStartButton.SearchProperties[WpfButton.PropertyNames.AutomationId] = "buttonA";
            }

    ```

13. W menu **kompilacja** wybierz polecenie **Kompiluj rozwiązanie**.

14. W Eksploratorze testów Uruchom okno CodedUITestMethod1.

     Tym razem kodowany test interfejsu użytkownika pomyślnie zakończy wszystkie etapy testu.  W oknie Wyniki testów zostanie wyświetlony stan **Zakończono**.

## <a name="external-resources"></a>Zasoby zewnętrzne

### <a name="videos"></a>Wideo
 ![link do](../data-tools/media/playvideo.gif "PlayVideo") [KODOWANYCH testów interfejsu użytkownika wideo — {-Episode1-GettingStarted](https://skydrive.live.com/?cid=2db0e1efe1c1d3b8&id=2DB0E1EFE1C1D3B8%21118)

 ![link do](../data-tools/media/playvideo.gif "PlayVideo") [KODOWANYCH testów interfejsu użytkownika wideo — {-Episode2-MaintainenceAndDebugging](https://skydrive.live.com/?cid=2db0e1efe1c1d3b8&id=2DB0E1EFE1C1D3B8%21116)

 ![link do](../data-tools/media/playvideo.gif "PlayVideo") [KODOWANYCH testów interfejsu użytkownika wideo — {-Episode3-HandCoding](https://skydrive.live.com/?cid=2db0e1efe1c1d3b8&id=2DB0E1EFE1C1D3B8%21117)

### <a name="hands-on-lab"></a>Ćwiczenia praktyczne
 [MSDN Virtual Lab: wprowadzenie do tworzenia kodowanych testów interfejsu użytkownika w programie Visual Studio 2010](https://windows.microsoft.com/en-US/windows/products/windows-media-player)

### <a name="faq"></a>Najczęściej zadawane pytania
 [Kodowane testy interfejsu użytkownika — często zadawane pytania — 1](https://blogs.msdn.com/b/mathew_aniyan/archive/tags/faq/)

 [Kodowane testy interfejsu użytkownika — często zadawane pytania — 2](https://social.msdn.microsoft.com/Forums/en-US/vsautotest/thread/3a74dd2c-cef8-4923-abbf-7a91f489e6c4)

### <a name="forum"></a>Forum
 [Testowanie automatyzacji interfejsu użytkownika programu Visual Studio (w tym CodedUI)](https://social.msdn.microsoft.com/Forums/en-US/vsautotest)

## <a name="see-also"></a>Zobacz też
 [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md) [wprowadzenie przy użyciu](https://msdn.microsoft.com/18e61d03-b96a-4058-a166-8ec6b3f6116b) [obsługiwanych konfiguracji i platform programu WPF Designer dla kodowanych testów interfejsu użytkownika i rejestrowania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md) [Edytowanie kodowanych testów interfejsu użytkownika za pomocą edytora kodowanego testu interfejsu użytkownika](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)
