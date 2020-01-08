---
title: Tworzenie kodowanego testu interfejsu użytkownika
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: f1e22a39035e5d3500f4dd45481319e1daecfa04
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592064"
---
# <a name="walkthrough-create-edit-and-maintain-a-coded-ui-test"></a>Przewodnik: Tworzenie, edytowanie i obsługa kodowanego testu interfejsu użytkownika

W tym instruktażu dowiesz się, jak tworzyć, edytować i obsługiwać kodowane testy interfejsu użytkownika w celu przetestowania aplikacji Windows Presentation Framework (WPF). Przewodnik zawiera rozwiązania do korygowania testów, które zostały naruszone przez różne problemy dotyczące chronometrażu i refaktoryzacji kontrolek.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="create-a-wpf-app"></a>Tworzenie aplikacji WPF

1. Utwórz nowy projekt **aplikacji WPF (.NET Framework)** i nadaj mu nazwę **SimpleWPFApp**.

     Zostanie otwarty **Projektant WPF** i zostanie wyświetlony MainWindow projektu.

2. Jeśli przybornik nie jest otwarty, otwórz go. Wybierz menu **Widok** , a następnie wybierz **Przybornik**.

3. W sekcji **wszystkie kontrolki WPF** przeciągnij **przycisk**, **pole wyboru** i formant **ProgressBar** na MainWindow na powierzchni projektowej.

4. Wybierz kontrolkę **przycisk** . W oknie **Właściwości** Zmień wartość właściwości **Nazwa** z \<nie > nazwy na Button1. Następnie zmień wartość właściwości **zawartość** z przycisku na Rozpocznij.

5. Wybierz formant **ProgressBar** . W oknie **Właściwości** Zmień wartość właściwości **Nazwa** z \<nie > nazwy na ProgressBar1. Następnie zmień wartość właściwości **Maximum** z **100** na **10000**.

6. Zaznacz kontrolkę **pola wyboru** . W oknie **Właściwości** Zmień wartość właściwości **Nazwa** z \<nie > nazwy na checkBox1 i wyczyść Właściwość **IsEnabled** .

     ![Prosta aplikacja WPF](../test/media/codedui_wpfapp.png)

7. Kliknij dwukrotnie formant przycisku, aby dodać program obsługi zdarzeń kliknięcia.

     *MainWindow.Xmal.cs* jest wyświetlany w edytorze kodu z kursorem w nowej metodzie Button1_Click.

8. W górnej części klasy MainWindow dodaj delegata. Delegat będzie używany dla paska postępu. Aby dodać delegata, dodaj następujący kod:

    ```csharp
    public partial class MainWindow : Window
    {
            private delegate void ProgressBarDelegate(System.Windows.DependencyProperty dp, Object value);

        public MainWindow()
        {

            InitializeComponent();
        }
    ```

9. W metodzie button1_Click dodaj następujący kod:

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

10. Zapisz plik.

### <a name="run-the-wpf-app"></a>Uruchamianie aplikacji WPF

1. W menu **Debuguj** wybierz polecenie **Rozpocznij debugowanie** lub naciśnij klawisz **F5**.

2. Zauważ, że formant pola wyboru jest wyłączony. Wybierz pozycję **Rozpocznij**.

     W ciągu kilku sekund pasek postępu powinien być zapełniony w 100%.

3. Teraz możesz wybrać kontrolkę pole wyboru.

4. Zamknij aplikację SimpleWPFApp.

## <a name="create-a-shortcut-to-the-wpf-app"></a>Tworzenie skrótu do aplikacji WPF

1. Znajdź utworzoną wcześniej aplikację SimpleWPFApp.

2. Utwórz na pulpicie skrót do aplikacji SimpleWPFApp. Kliknij prawym przyciskiem myszy *plik SimpleWPFApp. exe* i wybierz polecenie **Kopiuj**. Na pulpicie kliknij prawym przyciskiem myszy i wybierz polecenie **Wklej skrót**.

    > [!TIP]
    > Skrót do aplikacji ułatwia dodawanie lub modyfikowanie kodowanych testów interfejsu użytkownika dla aplikacji, ponieważ umożliwia szybkie uruchamianie aplikacji.

## <a name="create-a-coded-ui-test-for-simplewpfapp"></a>Tworzenie kodowanego testu interfejsu użytkownika dla SimpleWPFApp

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy rozwiązanie i wybierz polecenie **Dodaj** > **Nowy projekt**.

2. Wyszukaj i wybierz szablon projektu **kodowanego testu interfejsu użytkownika** , a następnie wykonaj kroki do momentu utworzenia projektu.

   > [!NOTE]
   > Jeśli nie widzisz **projekt testu kodowanego interfejsu użytkownika** szablonu, trzeba [instalacji składnika należy kodowanego testu interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component).

     Nowy projekt kodowanego testu interfejsu użytkownika o nazwie **CodedUITestProject1** jest dodawany do rozwiązania i zostanie wyświetlone okno dialogowe **generowanie kodu dla KODOWANEGO testu interfejsu użytkownika** .

1. Wybierz opcję **Rejestruj akcje, Edytuj mapę interfejsu użytkownika lub Dodaj potwierdzenia** , a następnie wybierz **przycisk OK**.

     Zostanie wyświetlone okno dialogowe **Konstruktor kodowanego testu interfejsu użytkownika UIMap** , a okno programu Visual Studio jest zminimalizowane.

     Aby uzyskać więcej informacji na temat opcji w oknie dialogowym, zobacz [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md).

1. Wybierz pozycję **Rozpocznij nagrywanie** w oknie dialogowym **Konstruktor KODOWANEGO testu interfejsu użytkownika UIMap** .

     ![Zacznij nagrywanie](../test/media/cuit_builder_record.png)

     Możesz wstrzymać nagrywanie, jeśli jest to konieczne, na przykład w przypadku konieczności zajmowania się pocztą przychodzącą.

     ![Wstrzymaj nagrywanie](../test/media/cuit_.png)

    > [!WARNING]
    > Wszystkie akcje wykonywane na pulpicie zostaną zarejestrowane. Wstrzymaj nagrywanie, jeśli wykonujesz akcje, które mogą prowadzić do zarejestrowania poufnych danych.

1. Uruchom SimpleWPFApp, używając skrótu na pulpicie.

     Tak jak wcześniej, Zauważ, że formant pola wyboru jest wyłączony.

1. Na SimpleWPFApp wybierz pozycję **Rozpocznij**.

     W ciągu kilku sekund pasek postępu powinien być zapełniony w 100%.

1. Zaznacz kontrolkę pole wyboru, która jest teraz włączona.

1. Zamknij aplikację SimpleWPFApp.

1. W oknie dialogowym **Konstruktor kodowanego testu interfejsu użytkownika UIMap** wybierz polecenie **Generuj kod**.

1. W polu **Nazwa metody** wpisz **SimpleAppTest** i wybierz polecenie **Dodaj i Generuj**. W ciągu kilku sekund zostanie wyświetlony kodowany test interfejsu użytkownika i zostanie on dodany do rozwiązania.

1. Zamknij **UIMap — Konstruktor kodowanego testu interfejsu użytkownika**.

     Plik *CodedUITest1.cs* pojawi się w edytorze kodu.

1. Zapisz projekt.

### <a name="run-the-test"></a>Uruchamianie testu

1. Z menu **test** wybierz pozycję **Windows** , a następnie wybierz **Eksplorator testów**.

2. Z **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.

3. W pliku *CodedUITest1.cs* Znajdź metodę **metodę CodedUITestMethod** , kliknij prawym przyciskiem myszy i wybierz polecenie **Uruchom testy**lub Uruchom test z **Eksploratora testów**.

   Podczas wykonywania kodowanego przebiegu testu interfejsu użytkownika aplikacja SimpleWPFApp jest widoczna. Wykonuje ona działania, których nie było w poprzedniej procedurze. Jednak gdy test próbuje zaznaczyć pole wyboru dla kontrolki pole wyboru, okno **wyniki testów** pokazuje, że test zakończył się niepowodzeniem. Jest to spowodowane tym, że test próbuje zaznaczyć pole wyboru, ale nie wie, że formant pola wyboru jest wyłączony, dopóki pasek postępu nie zostanie ukończony do 100%. Te i podobne problemy można rozwiązać, korzystając z różnych `UITestControl.WaitForControlXXX()` metod, które są dostępne dla kodowanego testowania interfejsu użytkownika. Kolejna procedura przedstawia użycie metody `WaitForControlEnabled()` w celu rozwiązania problemu, który spowodował niepowodzenie tego testu. Aby uzyskać więcej informacji, zobacz [wykonywanie kodowanych testów interfejsu użytkownika w przypadku określonych zdarzeń podczas odtwarzania](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md).

## <a name="edit-and-rerun-the-coded-ui-test"></a>Edytuj i ponownie uruchom kodowany test interfejsu użytkownika

1. W oknie **Eksplorator testów** wybierz test zakończony niepowodzeniem i w sekcji **ślad stosu** wybierz pierwszy link do **UIMap. SimpleAppTest ()** .

2. Plik *UIMap.Designer.cs* zostanie otwarty z punktem błędu wyróżnionego w kodzie:

    ```csharp
    // Select 'CheckBox' check box
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;
    ```

3. Aby rozwiązać ten problem, można wykonać kodowane testy interfejsu użytkownika, aby zaczekać na włączenie kontrolki CheckBox przed kontynuowaniem tego wiersza przy użyciu metody `WaitForControlEnabled()`.

    > [!WARNING]
    > Nie należy modyfikować pliku *UIMap.Designer.cs* . Wszelkie wprowadzone zmiany kodu zostaną nadpisywane przy każdym wygenerowaniu kodu za pomocą **konstruktora kodowanego testu interfejsu użytkownika UIMap**. Jeśli trzeba zmodyfikować nagraną metodę, skopiuj ją do pliku *UIMap.cs* i zmień jej nazwę. *UIMap.cs* pliku może służyć do zastępowania metod i właściwości w *UIMapDesigner.cs* pliku. Musisz usunąć odwołanie do oryginalnej metody w pliku *CodedUITest.cs* i zastąpić ją nazwą metody o zmienionej nazwie.

4. W **Eksplorator rozwiązań**Zlokalizuj *UIMap. UITest* w projekcie kodowanego testu interfejsu użytkownika.

5. Otwórz menu skrótów dla *UIMap. UITest* i wybierz polecenie **Otwórz**.

     Kodowany test interfejsu użytkownika jest wyświetlany w Edytorze kodowanego testu interfejsu użytkownika. Teraz można wyświetlać i edytować kodowany test interfejsu użytkownika.

6. W okienku **Akcja interfejsu użytkownika** wybierz metodę testową (SimpleAppTest), która ma zostać przeniesiona do pliku *UIMap.cs* lub *UIMap. vb* . Przeniesienie metody do innego pliku umożliwia dodanie niestandardowego kodu, który nie zostanie zastąpiony podczas ponownej kompilacji kodu testowego.

7. Wybierz przycisk **Przenieś kod** na pasku narzędzi **edytora KODOWANEGO testu interfejsu użytkownika** .

8. Pojawi się okno dialogowe programu Microsoft Visual Studio. Ostrzega o tym, że metoda zostanie przeniesiona z pliku *UIMap. UITest* do pliku *UIMap.cs* i nie będzie już można edytować metody przy użyciu edytora kodowanego testu interfejsu użytkownika. Wybierz **tak**.

     Metoda testowa jest usuwana z pliku *UIMap. UITest* i nie jest już wyświetlana w okienku Akcje interfejsu użytkownika. Aby edytować przeniesiony plik testowy, Otwórz plik *UIMap.cs* z **Eksplorator rozwiązań**.

9. Na pasku narzędzi programu Visual Studio wybierz pozycję **Zapisz**.

     Aktualizacje metody testowej są zapisywane w pliku *UIMap. Designer* .

    > [!WARNING]
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

13. W pliku *CodedUITest1.cs* Znajdź metodę **metodę CodedUITestMethod** i Dodaj komentarz lub Zmień nazwę odwołania na oryginalną metodę SimpleAppTest (), a następnie zastąp ją nowym ModifiedSimpleAppTest ():

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

16. Tym razem kodowany test interfejsu użytkownika pomyślnie zakończy wszystkie kroki testu, a w oknie **Eksplorator testów** zostanie wyświetlony komunikat **zakończony powodzeniem** .

## <a name="refactor-a-control-in-simplewpfapp"></a>Refaktoryzacja kontrolki w SimpleWPFApp

1. W pliku *MainWindow. XAML* w Projektancie wybierz formant Button.

2. W górnej części okna **Właściwości** Zmień wartość właściwości **Nazwa** z **Button1** na **Button**.

3. W menu **kompilacja** wybierz polecenie **Kompiluj rozwiązanie**.

4. W **Eksploratorze testów**Uruchom **okno CodedUITestMethod1**.

     Test zakończy się niepowodzeniem, ponieważ w UIMap jako button1 kodowany test interfejsu użytkownika nie można znaleźć formantu przycisku, który pierwotnie był mapowany. Refaktoryzacja może w ten sposób wpłynąć na kodowane testy interfejsu użytkownika.

5. W **Eksploratorze testów**w sekcji **ślad stosu** wybierz pierwsze łącze obok **UIMpa. ModifiedSimpleAppTest ()** .

     Zostanie otwarty plik *UIMap.cs* . Punkt błędu jest wyróżniany w kodzie:

    ```csharp
    // Click 'Start' button
    Mouse.Click(uIStartButton, new Point(27, 10));
    ```

     Należy zauważyć, że wiersz kodu we wcześniejszej części tej procedury używa `UiStartButton`, czyli nazwy UIMap przed przeprowadzeniem jej refaktoryzacji.

     Aby rozwiązać ten problem, można dodać formant refaktoryzacji do UIMap przy użyciu **konstruktora kodowanego testu interfejsu użytkownika**. Możesz zaktualizować kod testu, aby użyć kodu, jak pokazano w następnej procedurze.

## <a name="map-refactored-control-rerun-the-test"></a>Kontrolka refaktoryzacji mapy ponownie uruchamia test

1. W pliku *CodedUITest1.cs* , w metodzie **okno CodedUITestMethod1 ()** , kliknij prawym przyciskiem myszy pozycję **Generuj kod dla kodowanego testu interfejsu użytkownika** , a następnie wybierz opcję **Użyj konstruktora kodowanego testu interfejsu użytkownika**.

     Zostanie wyświetlony **Konstruktor kodowanego testu interfejsu użytkownika UIMap** .

2. Korzystając ze utworzonego wcześniej skrótu pulpitu, uruchom utworzoną wcześniej aplikację SimpleWPFApp.

3. W oknie dialogowym **Konstruktor kodowanego testu interfejsu użytkownika UIMap** Przeciągnij narzędzie krzyżyka do przycisku **Start** w SimpleWPFApp.

     Przycisk **Start** znajduje się w niebieskim polu. **Konstruktor kodowanego testu interfejsu użytkownika** zajmuje kilka sekund, aby przetworzyć dane dla wybranej kontrolki i wyświetlić właściwości kontrolki. Zwróć uwagę, że wartość **AutomationUId** jest **przyciskiem**.

4. We właściwościach formantu wybierz strzałkę w lewym górnym rogu, aby rozwinąć Mapę formantów UI. Zauważ, że wybrano **UIStartButton1** .

5. Na pasku narzędzi wybierz **mapę Dodaj formant do kontrolki interfejsu użytkownika**.

     Stan u dołu okna weryfikuje akcję, wyświetlając **wybrany formant został dodany do mapy formantów interfejsu użytkownika**.

6. W oknie dialogowym **Konstruktor kodowanego testu interfejsu użytkownika UIMap** wybierz polecenie **Generuj kod**.

     **Kreator kodowanego testu interfejsu użytkownika — okno dialogowe generowanie kodu** pojawia się z adnotacją wskazującą, że nie jest wymagana żadna Nowa metoda, a ten kod zostanie wygenerowany tylko dla zmian w mapie formantów interfejsu użytkownika.

7. Wybierz pozycję **Generuj**.

8. Zamknij aplikację SimpleWPFApp.

9. Zamknij **UIMap — Konstruktor kodowanego testu interfejsu użytkownika**.

10. W **Eksplorator rozwiązań**otwórz plik *UIMap.Designer.cs* .

11. W pliku *UIMap.Designer.cs* Znajdź właściwość **UIStartButton1** . Zauważ, że `SearchProperties` jest ustawiona na `"buttonA"`:

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

     Teraz można zmodyfikować kodowany test interfejsu użytkownika do korzystania z ostatnio mapowanego formantu. Jak wskazano w poprzedniej procedurze, jeśli chcesz przesłonić wszelkie metody lub właściwości w kodowanym teście interfejsu użytkownika, należy to zrobić w pliku *UIMap.cs* .

12. W pliku *UIMap.cs* Dodaj konstruktora i określ Właściwość `SearchProperties` właściwości `UIStartButton`, aby użyć właściwości `AutomationID` z wartością `"buttonA":`

    ```csharp
    public UIMap()
            {
                this.UIMainWindowWindow.UIStartButton.SearchProperties[WpfButton.PropertyNames.AutomationId] = "buttonA";
            }
    ```

13. W menu **kompilacja** wybierz polecenie **Kompiluj rozwiązanie**.

14. W **Eksploratorze testów**Uruchom **okno CodedUITestMethod1**.

     Tym razem kodowany test interfejsu użytkownika pomyślnie zakończy wszystkie etapy testu. W oknie **wyniki testów** zostanie wyświetlony stan **Zakończono**.

## <a name="videos"></a>Wideo

![link do wideo](../data-tools/media/playvideo.gif) [wprowadzenie do kodowanych testów interfejsu użytkownika](https://onedrive.live.com/?id=2DB0E1EFE1C1D3B8%21110&cid=2DB0E1EFE1C1D3B8)

## <a name="faq"></a>Najczęściej zadawane pytania

[Kodowane testy interfejsu użytkownika — często zadawane pytania](https://social.msdn.microsoft.com/Forums/vsautotest/3a74dd2c-cef8-4923-abbf-7a91f489e6c4/faqs)

## <a name="see-also"></a>Zobacz także

- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
- [Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i nagrywania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [Edytowanie kodowanych testów interfejsu użytkownika za pomocą edytora kodowanego testu interfejsu użytkownika](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)
