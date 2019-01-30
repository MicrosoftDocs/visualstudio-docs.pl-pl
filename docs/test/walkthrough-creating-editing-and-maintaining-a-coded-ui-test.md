---
title: Tworzenie kodowanego testu interfejsu użytkownika
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: d7659de6e90ca13172459b1bcc1e305e14a91cfc
ms.sourcegitcommit: a916ce1eec19d49f060146f7dd5b65f3925158dd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2019
ms.locfileid: "55231964"
---
# <a name="walkthrough-create-edit-and-maintain-a-coded-ui-test"></a>Przewodnik: Tworzenie, edytowanie i obsługa kodowanego testu interfejsu użytkownika

W tym przewodniku dowiesz się, jak tworzenie, edytowanie i obsługa kodowanego interfejsu użytkownika testu do testowania aplikacji Windows Presentation Framework (WPF). Dostarcza on rozwiązania do korekcji testów, które zostały uszkodzone przez różne problemy dotyczące synchronizacji i refaktoryzacją kontroli.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="create-a-wpf-app"></a>Tworzenie aplikacji WPF

1.  Na **pliku** menu wskaż **New**, a następnie wybierz pozycję **projektu**.

     **Nowy projekt** pojawi się okno dialogowe.

2.  W **zainstalowane** okienku rozwiń **Visual C#**, a następnie wybierz pozycję **pulpitu Windows**.

3.  Nad środkowym okienkiem Sprawdź, czy ma wartość listy rozwijanej target framework **.NET Framework 4.5**.

4.  W środkowym okienku wybierz **aplikacji WPF** szablonu.

5.  W **nazwa** polu tekstowym **SimpleWPFApp**.

6.  Wybierz folder, w którym zapiszesz projekt. W **lokalizacji** tekstu wpisz nazwę folderu.

7.  Wybierz **OK**.

     **WPF Designer for Visual Studio** otwiera i wyświetla główne okno projektu.

8.  Jeśli przybornik nie jest otwarty, otwórz go. Wybierz **widoku** menu, a następnie wybierz **przybornika**.

9. W obszarze **wszystkie formanty WPF** sekcji, przeciągnij **przycisk**, **wyboru** i **ProgressBar** projektową okna głównego w projekcie powierzchni.

10. Wybierz **przycisk** kontroli. W **właściwości** okna, zmień wartość **nazwa** właściwości z \<Brak nazwy > na button1. Następnie zmień wartość **zawartości** właściwość przycisk do ekranu startowego.

11. Wybierz **ProgressBar** kontroli. W **właściwości** okna, zmień wartość **nazwa** właściwość \<Brak nazwy > na progressBar1. Następnie zmień wartość **maksymalna** właściwość **100** do **10000**.

12. Wybierz **wyboru** kontroli. W **właściwości** okna, zmień wartość **nazwa** właściwość \<Brak nazwy > checkBox1 i wyczyść **IsEnabled** właściwości.

     ![Prostej aplikacji WPF](../test/media/codedui_wpfapp.png)

13. Kliknij dwukrotnie formant przycisku aby dodać obsługę zdarzeń kliknięcia.

     *MainWindow.xmal.cs* jest wyświetlany w edytorze kodu z kursorem w nowej metodzie button1_Click.

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

### <a name="run-the-wpf-app"></a>Uruchamianie aplikacji WPF

1.  Na **debugowania** menu, wybierz opcję **Rozpocznij debugowanie** lub naciśnij **F5**.

2.  Należy zauważyć, że kontrolka pola wyboru jest wyłączona. Wybierz **Start**.

     W ciągu kilku sekund pasek postępu powinien być zapełniony w 100%.

3.  Możesz teraz wybrać kontrolkę pola wyboru.

4.  Zamknij aplikację SimpleWPFApp.

## <a name="create-a-shortcut-to-the-wpf-app"></a>Utwórz skrót do aplikacji WPF

1.  Znajdź aplikację SimpleWPFApp, która została utworzona wcześniej.

2.  Utwórz na pulpicie skrót do aplikacji SimpleWPFApp. Kliknij prawym przyciskiem myszy *SimpleWPFApp.exe* i wybierz polecenie **kopiowania**. Na pulpicie kliknij prawym przyciskiem myszy i wybierz polecenie **Wklej skrót**.

    > [!TIP]
    > Skrót do aplikacji ułatwia dodawanie lub modyfikowanie kodowanych testów interfejsu użytkownika dla aplikacji, ponieważ pozwala to na szybkie uruchamianie aplikacji.

## <a name="create-a-coded-ui-test-for-simplewpfapp"></a>Tworzenie kodowanego testu interfejsu użytkownika dla aplikacji SimpleWPFApp

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie, wybierz pozycję **Dodaj** , a następnie wybierz **nowy projekt**.

     **Dodaj nowy projekt** pojawi się okno dialogowe.

1. W **zainstalowane** okienku rozwiń **Visual C#**, a następnie wybierz pozycję **testu**.

1. W środkowym okienku wybierz **projekt kodowanego testu interfejsu użytkownika** szablonu.

   > [!NOTE]
   > Jeśli nie widzisz **projekt testu kodowanego interfejsu użytkownika** szablonu, trzeba [instalacji składnika należy kodowanego testu interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component).

1. Wybierz **OK**.

     Nowy kodowanego testu interfejsu użytkownika o nazwie **CodedUITestProject1** jest dodawany do rozwiązania.

     **Generuj kod dla kodowanego testu interfejsu użytkownika** pojawi się okno dialogowe.

1. Wybierz **Rejestruj akcje, Edytuj mapę interfejsu użytkownika lub Dodaj potwierdzenia** opcji, a następnie wybierz **OK**.

     **UIMap — Konstruktor kodowanego testu interfejsu użytkownika** zostanie wyświetlone okno dialogowe i okna programu Visual Studio jest zminimalizowany.

     Aby uzyskać więcej informacji na temat opcji w oknie dialogowym, zobacz [tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md).

1. Wybierz **Rozpocznij nagrywanie** na **UIMap — Konstruktor kodowanego testu interfejsu użytkownika** okna dialogowego.

     ![Zacznij nagrywanie](../test/media/cuit_builder_record.png)

     Można zatrzymać nagrywanie, jeśli to konieczne, na przykład jeśli masz do czynienia z przychodzących wiadomości e-mail.

     ![Wstrzymanie nagrywania](../test/media/cuit_.png)

    > [!WARNING]
    > Wszystkie akcje wykonywane na pulpicie będą rejestrowane. Wstrzymanie nagrywania, jeśli są wykonywane działania, które mogą prowadzić do danych poufnych jest zawarty w nagraniu.

1. Uruchamianie aplikacji za pomocą skrótu na pulpicie.

     Tak jak poprzednio Zwróć uwagę, że kontrolka pola wyboru jest wyłączona.

1. W aplikacji, wybierz **Start**.

     W ciągu kilku sekund pasek postępu powinien być zapełniony w 100%.

1. Zaznacz formant pola wyboru, która jest teraz włączony.

1. Zamknij aplikację SimpleWPFApp.

1. Na **UIMap — Konstruktor kodowanego testu interfejsu użytkownika** okno dialogowe, wybierz **Generuj kod**.

1. W **nazwę metody** wpisz **SimpleAppTest** i wybierz polecenie **Dodaj i Generuj**. W ciągu kilku sekund kodowany test interfejsu użytkownika pojawi się i zostanie dodany do rozwiązania.

1. Zamknij **UIMap - kodowanego konstruktora testu interfejsu użytkownika**.

     *CodedUITest1.cs* plik pojawia się w edytorze kodu.

1. Zapisz projekt.

### <a name="run-the-test"></a>Uruchom test

1. Z **testu** menu, wybierz **Windows** , a następnie wybierz **Eksplorator testów**.

2. Z **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.

3. W *CodedUITest1.cs* plików, zlokalizuj **CodedUITestMethod** , kliknij prawym przyciskiem myszy i wybierz opcję **Uruchom testy**, lub uruchomić test z **Eksploratora testów**.

   Podczas wykonywania kodowanego przebiegu testu interfejsu użytkownika aplikacja SimpleWPFApp jest widoczna. Wykonuje ona działania, których nie było w poprzedniej procedurze. Jednak gdy test próbuje zaznaczyć pole wyboru, formantu pola wyboru **wyników testu** okno pokazuje, że test nie powiódł się. Ponieważ test próbuje zaznaczyć pole wyboru, ale nie ma informacji, że kontrolka pola wyboru jest wyłączona, dopóki pasek postępu nie zostanie zapełniony w 100%. Możesz rozwiązać ten i podobne problemy za pomocą różnych `UITestControl.WaitForControlXXX()` metod, które są dostępne dla kodowanego testowania interfejsu użytkownika. Następna procedura wykaże za pomocą `WaitForControlEnabled()` metodę, aby rozwiązać ten problem, który spowodował niepowodzenie testu. Aby uzyskać więcej informacji, zobacz [utworzyć kodowane testy interfejsu użytkownika oczekiwania dla określonych zdarzeń podczas odtwarzania](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md).

## <a name="edit-and-rerun-the-coded-ui-test"></a>Edytowanie i ponowne uruchamianie kodowanego testu interfejsu użytkownika

1.  W **Eksploratora testów** okna, wybierz test zakończony niepowodzeniem i **ślad stosu** sekcji, wybierz pierwsze łącze do **UIMap.SimpleAppTest()**.

2.  *UIMap.Designer.cs* plik otwiera się z punktem błędu wyróżnionego w kodzie:

    ```csharp
    // Select 'CheckBox' check box
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;
    ```

3.  Aby rozwiązać ten problem, może wykonać kodowany test interfejsu użytkownika, poczekaj, aż formant CheckBox zostanie włączony przed przejściem do tego wiersza przy użyciu `WaitForControlEnabled()` metody.

    > [!WARNING]
    > Nie należy modyfikować *UIMap.Designer.cs* pliku. Dowolny kod wprowadzonych zmian zostaną zastąpione każdorazowo po wygenerowaniu kodu za pomocą **UIMap — Konstruktor kodowanego testu interfejsu użytkownika**. Jeśli trzeba zmodyfikować nagraną metodę, skopiuj go do *UIMap.cs* plików i zmień jego nazwę. *UIMap.cs* pliku może służyć do zastępowania metod i właściwości w *UIMapDesigner.cs* pliku. Musisz usunąć odwołanie do oryginalnej metody w *CodedUITest.cs* plik i zastąp go nazwą metody o zmienionej nazwie.

4.  W **Eksploratora rozwiązań**, zlokalizuj *UIMap.uitest* w projekt kodowanego testu interfejsu użytkownika.

5.  Otwórz menu skrótów dla *UIMap.uitest* i wybierz polecenie **Otwórz**.

     Kodowany test interfejsu użytkownika jest wyświetlany w Edytorze kodowanego testu interfejsu użytkownika. Teraz można wyświetlać i edytować kodowany test interfejsu użytkownika.

6.  W **działania interfejsu użytkownika** okienku zaznacz metody testowej (SimpleAppTest), który chcesz przenieść do *UIMap.cs* lub *UIMap.vb* pliku. Przenoszenie metody do innego pliku umożliwia kod niestandardowy do dodania, który nie jest zastępowana kod testu jest ponownie kompilowana.

7.  Wybierz **Przenieś kod** znajdujący się na **edytora kodowanego testu interfejsu użytkownika** paska narzędzi.

8.  Pojawi się okno dialogowe programu Microsoft Visual Studio. Zawiera ono ostrzeżenie, że metoda ma zostać przeniesiona z *UIMap.uitest* plik *UIMap.cs* plik i że nie będzie można edytować metody za pomocą edytora kodowanego testu interfejsu użytkownika. Wybierz **tak**.

     Metoda testowa jest usuwany z *UIMap.uitest* pliku i nie jest już wyświetlana w okienku Akcje interfejsu użytkownika. Aby edytować przeniesiony plik testowy, otwórz *UIMap.cs* plik wchodzącej w skład **Eksploratora rozwiązań**.

9. Na pasku narzędzi programu Visual Studio wybierz **Zapisz**.

     Aktualizacje do metody testowej są zapisywane w *UIMap.Designer* pliku.

    > [!WARNING]
    > Po przeniesieniu metody nie będzie można edytować jej za pomocą Edytora kodowanego testu interfejsu użytkownika. Należy dodać niestandardowy kod i obsługiwać go za pomocą Edytora kodu.

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

13. W *CodedUITest1.cs* plików, zlokalizuj **CodedUITestMethod** metody, a następnie przekształcić w komentarz lub zmień nazwę odniesienia do oryginalnej metody SimpleAppTest() i zastąp go przy użyciu nowego Testem ModifiedSimpleAppTest():

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

16. Tym razem kodowany test interfejsu użytkownika pomyślnie zakończy wszystkie etapy testu, i **zakończone powodzeniem** jest wyświetlany w **Eksploratora testów** okna.

## <a name="refactor-a-control-in-simplewpfapp"></a>Reorganizacja formantu w aplikacji SimpleWPFApp

1.  W *MainWindow.xaml* pliku w Projektancie zaznacz formant przycisku.

2.  W górnej części **właściwości** oknie zmiany **nazwa** wartość właściwości z **button1** do **buttonA**.

3.  Na **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.

4.  W **Eksplorator testów**Uruchom **CodedUITestMethod1**.

     Test zakończy się niepowodzeniem, ponieważ w UIMap jako button1 kodowany test interfejsu użytkownika nie można znaleźć formantu przycisku, który pierwotnie był mapowany. Refaktoryzacja może w ten sposób wpłynąć na kodowane testy interfejsu użytkownika.

5.  W **Eksplorator testów**w **ślad stosu** sekcji, wybierz pierwsze łącze obok **(UIMpa.ModifiedSimpleAppTest)**.

     *UIMap.cs* plik zostanie otwarty. Punkt błędu jest wyróżniany w kodzie:

    ```csharp
    // Click 'Start' button
    Mouse.Click(uIStartButton, new Point(27, 10));
    ```

     Należy zauważyć, że w wierszu kodu wcześniej w tej procedurze jest przy użyciu `UiStartButton`, która była nazwą UIMap, zanim został wycofany.

     Aby rozwiązać ten problem, można dodać wycofany formant do UIMap za pomocą **kodowanego testu interfejsu użytkownika**. Możesz zaktualizować kod testu do użycia w kodzie, jak pokazano w następnej procedurze.

## <a name="map-refactored-control-rerun-the-test"></a>Mapowanie wycofanej kontroli Uruchom ponownie test

1.  W *CodedUITest1.cs* pliku w **CodedUITestMethod1()** metody, kliknij prawym przyciskiem myszy, wybierz opcję **Generuj kod dla kodowanego testu interfejsu użytkownika** , a następnie wybierz **użycia Konstruktor kodowanego testu interfejsu użytkownika**.

     **UIMap — Konstruktor kodowanego testu interfejsu użytkownika** pojawia się.

2.  Przy użyciu utworzonego wcześniej skrótu na pulpicie, uruchom aplikację SimpleWPFApp, która została utworzona wcześniej.

3.  Na **UIMap — Konstruktor kodowanego testu interfejsu użytkownika** okno dialogowe, przeciągnij narzędzie krzyżyka do **Start** przycisk na SimpleWPFApp.

     **Start** przycisk jest ujęty w niebieskie pole. **Konstruktor kodowanego testu interfejsu użytkownika** zajmuje kilka sekund, aby przetwarzać dane dla wybranej kontrolki i wyświetlić właściwości formantu. Należy zauważyć, że wartość **AutomationUId** jest **buttonA**.

4.  We właściwościach formantu wybierz strzałkę w lewym górnym rogu, aby rozwinąć Mapę formantów UI. Należy zauważyć, że **UIStartButton1** jest zaznaczone.

5.  Na pasku narzędzi wybierz **dodać formant do mapy formantów UI**.

     Stan w dolnej części okna sprawdza akcję poprzez wyświetlenie **zaznaczony formant został dodany do mapy formantów UI**.

6.  Na **UIMap — Konstruktor kodowanego testu interfejsu użytkownika** okno dialogowe, wybierz **Generuj kod**.

     **Kodowanego testu interfejsu użytkownika — Generuj kod** zostanie wyświetlone okno dialogowe z notatki z informacją, że żadna nowa metoda jest wymagany, a kod zostanie wygenerowany tylko zmiany mapy formantów interfejsu użytkownika.

7.  Wybierz **Generowanie**.

8.  Zamknij aplikację SimpleWPFApp.

9. Zamknij **UIMap - kodowanego konstruktora testu interfejsu użytkownika**.

10. W **Eksploratora rozwiązań**, otwórz *UIMap.Designer.cs* pliku.

11. W *UIMap.Designer.cs* plików, zlokalizuj **UIStartButton1** właściwości. Zwróć uwagę `SearchProperties` ustawiono `"buttonA"`:

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

     Teraz można zmodyfikować kodowany test interfejsu użytkownika do korzystania z ostatnio mapowanego formantu. Jak wskazano się w poprzedniej procedurze, aby zastąpić jakąkolwiek metodę lub właściwości w kodowanym teście interfejsu użytkownika, należy więc w *UIMap.cs* pliku.

12. W *UIMap.cs* pliku, Dodaj Konstruktor i określ `SearchProperties` właściwość `UIStartButton` właściwości, aby korzystała `AutomationID` właściwość z wartością `"buttonA":`

    ```csharp
    public UIMap()
            {
                this.UIMainWindowWindow.UIStartButton.SearchProperties[WpfButton.PropertyNames.AutomationId] = "buttonA";
            }
    ```

13. Na **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.

14. W **Eksplorator testów**Uruchom **CodedUITestMethod1**.

     Tym razem kodowany test interfejsu użytkownika pomyślnie zakończy wszystkie etapy testu. W **wyniki testów** oknie zostanie wyświetlony stan **zakończone powodzeniem**.

## <a name="videos"></a>Wideo

![Link do klipu wideo](../data-tools/media/playvideo.gif) [wprowadzenie kodowane testy interfejsu użytkownika](https://onedrive.live.com/?id=2DB0E1EFE1C1D3B8%21110&cid=2DB0E1EFE1C1D3B8)

## <a name="faq"></a>Najczęściej zadawane pytania

[Kodowane testy interfejsu użytkownika — często zadawane pytania](https://social.msdn.microsoft.com/Forums/vsautotest/3a74dd2c-cef8-4923-abbf-7a91f489e6c4/faqs)

## <a name="see-also"></a>Zobacz także

- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
- [Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i nagrywania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [Edytowanie kodowanych testów interfejsu użytkownika za pomocą edytora kodowanego testu interfejsu użytkownika](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)
