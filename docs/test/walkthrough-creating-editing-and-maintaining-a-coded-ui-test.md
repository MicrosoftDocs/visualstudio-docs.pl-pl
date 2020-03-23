---
title: Tworzenie zakodowany test interfejsu użytkownika
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: f1e22a39035e5d3500f4dd45481319e1daecfa04
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75592064"
---
# <a name="walkthrough-create-edit-and-maintain-a-coded-ui-test"></a>Instruktaż: Tworzenie, edytowanie i obsługa zakodowany test interfejsu użytkownika

W tym instruktażu dowiesz się, jak utworzyć, edytować i obsługiwać kodowany test interfejsu użytkownika, aby przetestować aplikację Windows Presentation Framework (WPF). Przewodnik zawiera rozwiązania do korygowania testów, które zostały przerwane przez różne problemy z chronometrażu i refaktoryzacji formantów.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="create-a-wpf-app"></a>Tworzenie aplikacji WPF

1. Utwórz nowy projekt **aplikacji WPF (.NET Framework)** i nazwij go **SimpleWPFApp**.

     **WPF Projektant** otwiera i wyświetla MainWindow projektu.

2. Jeśli przybornik nie jest otwarty, otwórz go. Wybierz menu **Widok,** a następnie wybierz polecenie **Przybornik**.

3. W sekcji **Wszystkie formanty WPF** przeciągnij kontrolkę **Button**, **CheckBox** i **ProgressBar** na mainwindow na powierzchni projektowej.

4. Wybierz kontrolka **Przycisk.** W oknie **Właściwości** zmień wartość właściwości Name \<z **No** Name> na button1. Następnie zmień wartość właściwości **Content** z Button na Start.

5. Wybierz kontrolka **ProgressBar.** W oknie **Właściwości** zmień wartość właściwości **Name** \<z No Name> progressBar1. Następnie zmień wartość właściwości **Maximum** ze **100** na **10000**.

6. Zaznacz **kontrolkę Pole wyboru.** W oknie **Właściwości** zmień wartość właściwości Name \<z **No** Name> na checkBox1 i wyczyść właściwość **IsEnabled.**

     ![Prosta aplikacja WPF](../test/media/codedui_wpfapp.png)

7. Kliknij dwukrotnie kontrolkę przycisku, aby dodać program obsługi zdarzeń kliknięć.

     *MainWindow.xmal.cs* jest wyświetlany w Edytorze kodu z kursorem w nowej button1_Click metody.

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

1. W menu **Debugowanie** wybierz polecenie **Rozpocznij debugowanie** lub naciśnij **klawisz F5**.

2. Należy zauważyć, że formant pola wyboru jest wyłączony. Wybierz **pozycję Start**.

     W ciągu kilku sekund pasek postępu powinien być zapełniony w 100%.

3. Teraz można zaznaczyć kontrolkę pola wyboru.

4. Zamknij aplikację SimpleWPFApp.

## <a name="create-a-shortcut-to-the-wpf-app"></a>Tworzenie skrótu do aplikacji WPF

1. Znajdź aplikację SimpleWPFApp, która została utworzona wcześniej.

2. Utwórz na pulpicie skrót do aplikacji SimpleWPFApp. Kliknij prawym przyciskiem myszy *simplewpfapp.exe* i wybierz polecenie **Kopiuj**. Na pulpicie kliknij prawym przyciskiem myszy i wybierz polecenie **Wklej skrót**.

    > [!TIP]
    > Skrót do aplikacji ułatwia dodawanie lub modyfikowanie kodowanych testów interfejsu użytkownika dla aplikacji, ponieważ umożliwia szybkie uruchomienie aplikacji.

## <a name="create-a-coded-ui-test-for-simplewpfapp"></a>Tworzenie kodowanych testów interfejsu użytkownika dla SimpleWPFApp

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy rozwiązanie i wybierz polecenie **Dodaj** > **nowy projekt**.

2. Wyszukaj i wybierz szablon **projektu projektu testu kodowany** interfejs użytkownika i kontynuuj przebieg kroków, aż zostanie utworzony projekt.

   > [!NOTE]
   > Jeśli nie widzisz szablonu **projektu testu kodowany** interfejs użytkownika, musisz [zainstalować zakodowany składnik testu interfejsu użytkownika.](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component)

     Nowy kodowany projekt testu interfejsu użytkownika o nazwie **CodedUITestProject1** jest dodawany do rozwiązania i pojawi się okno dialogowe **Generowanie kodu dla testu interfejsu użytkownika kodowane.**

1. Wybierz opcję **Nagraj akcje, edytuj mapę interfejsu użytkownika lub dodaj potwierdzenia** i wybierz przycisk **OK**.

     Zostanie wyświetlone okno **konstruktora testów interfejsu użytkownika kodowanego,** a okno programu Visual Studio zostanie zminimalizowane.

     Aby uzyskać więcej informacji na temat opcji w oknie dialogowym, zobacz [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md).

1. Wybierz **pozycję Rozpocznij nagrywanie** w oknie dialogowym **Konstruktora testów interfejsu użytkownika kodowany.**

     ![Rozpocznij nagrywanie](../test/media/cuit_builder_record.png)

     W razie potrzeby można wstrzymać nagrywanie, na przykład jeśli masz do czynienia z pocztą przychodzącą.

     ![Wstrzymanie nagrywania](../test/media/cuit_.png)

    > [!WARNING]
    > Wszystkie czynności wykonywane na pulpicie zostaną zarejestrowane. Wstrzymaj nagrywanie, jeśli wykonujesz akcje, które mogą prowadzić do włączenia poufnych danych do nagrania.

1. Uruchom SimpleWPFApp za pomocą skrótu na pulpicie.

     Tak jak poprzednio, należy zauważyć, że formant pola wyboru jest wyłączony.

1. W aplikacji SimpleWPFApp wybierz pozycję **Start**.

     W ciągu kilku sekund pasek postępu powinien być zapełniony w 100%.

1. Zaznacz formant pola wyboru, który jest teraz włączony.

1. Zamknij aplikację SimpleWPFApp.

1. W oknie dialogowym **Konstruktora testów interfejsu użytkownika kodowany** wybierz pozycję **Generuj kod**.

1. W polu **Nazwa metody** wpisz **SimpleAppTest** i wybierz pozycję **Dodaj i wygeneruj**. W ciągu kilku sekund pojawi się kodowany test interfejsu użytkownika i zostanie dodany do rozwiązania.

1. Zamknij **UIMap - Kodowany konstruktor testów interfejsu użytkownika**.

     Plik *CodedUITest1.cs* pojawi się w edytorze kodu.

1. Zapisz swój projekt.

### <a name="run-the-test"></a>Uruchamianie testu

1. Z menu **Testuj** wybierz pozycję **Windows,** a następnie wybierz polecenie **Eksplorator testów**.

2. Z menu **Kompilacja** wybierz polecenie **Build Solution**.

3. W pliku *CodedUITest1.cs* zlokalizuj metodę **Metody Metody Kodowania IITestMethod,** kliknij prawym przyciskiem myszy i wybierz polecenie **Uruchom testy**lub uruchom test z **Eksploratora testów**.

   Podczas wykonywania kodowanego przebiegu testu interfejsu użytkownika aplikacja SimpleWPFApp jest widoczna. Wykonuje ona działania, których nie było w poprzedniej procedurze. Jednak gdy test próbuje zaznaczyć pole wyboru dla formantu pola wyboru, okno **Wyniki testu** pokazuje, że test nie powiódł się. Dzieje się tak, ponieważ test próbuje zaznaczyć pole wyboru, ale nie jest świadomy, że formant pola wyboru jest wyłączony, dopóki pasek postępu nie zostanie ukończony w 100%. Można rozwiązać ten i podobne problemy `UITestControl.WaitForControlXXX()` przy użyciu różnych metod, które są dostępne dla kodowanych testów interfejsu użytkownika. Następna procedura zademonstruje przy użyciu metody, `WaitForControlEnabled()` aby rozwiązać problem, który spowodował niepowodzenie tego testu. Aby uzyskać więcej informacji, zobacz [Aby kodowane testy interfejsu użytkownika czekały na określone zdarzenia podczas odtwarzania](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md).

## <a name="edit-and-rerun-the-coded-ui-test"></a>Edytowanie i ponowne odtwarzanie kodowanych testów interfejsu użytkownika

1. W oknie **Eksploratora testów** wybierz test nieudolny, a w sekcji **StackTrace** wybierz pierwsze łącze do **UIMap.SimpleAppTest().**

2. Plik *UIMap.Designer.cs* zostanie otwarty z wyróżnionym punktem błędu w kodzie:

    ```csharp
    // Select 'CheckBox' check box
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;
    ```

3. Aby rozwiązać ten problem, można wykonać kodowany test interfejsu użytkownika czekać na checkbox formant, `WaitForControlEnabled()` aby włączyć przed kontynuowaniem w tym wierszu przy użyciu metody.

    > [!WARNING]
    > Nie należy modyfikować pliku *UIMap.Designer.cs.* Wszelkie wprowadzone zmiany kodu zostaną zastąpione za każdym razem, gdy wygenerujesz kod za pomocą **UIMap - Coded UI Test Builder**. Jeśli musisz zmodyfikować zarejestrowaną metodę, skopiuj ją do *pliku UIMap.cs* i zmień jego nazwę. UIMap.cs *UIMap.cs* plik może służyć do zastępowania metod i właściwości w pliku *UIMapDesigner.cs.* Należy usunąć odwołanie do oryginalnej metody w pliku *CodedUITest.cs* i zastąpić go nazwą metody o zmienionej nazwie.

4. W **Eksploratorze rozwiązań**zlokalizuj *UIMap.uitest* w kodowanym projekcie testowym interfejsu użytkownika.

5. Otwórz menu skrótów dla *UIMap.uitest* i wybierz pozycję **Otwórz**.

     Kodowany test interfejsu użytkownika jest wyświetlany w Edytorze kodowanego testu interfejsu użytkownika. Teraz można wyświetlać i edytować kodowany test interfejsu użytkownika.

6. W okienku **Akcja interfejsu** użytkownika wybierz metodę testową (SimpleAppTest), którą chcesz przenieść do *pliku UIMap.cs* lub *UIMap.vb.* Przeniesienie metody do innego pliku umożliwia niestandardowy kod, który nie zostanie zastąpiony, gdy kod testowy zostanie ponownie skompilowany.

7. Wybierz przycisk **Przenieś kod** na pasku narzędzi **Edytora testów kodowanych** interfejsu użytkownika.

8. Pojawi się okno dialogowe programu Microsoft Visual Studio. Ostrzega, że metoda zostanie przeniesiona z pliku *UIMap.uitest* do pliku *UIMap.cs* i że nie będzie już można edytować metody przy użyciu edytora testów kodowanych interfejsu użytkownika. Wybierz **pozycję Tak**.

     Metoda testowa jest usuwana z pliku *UIMap.uitest* i nie jest już wyświetlana w okienku Akcje interfejsu użytkownika. Aby edytować przeniesiony plik testowy, otwórz plik *UIMap.cs* z **Eksploratora rozwiązań**.

9. Na pasku narzędzi Programu Visual Studio wybierz pozycję **Zapisz**.

     Aktualizacje metody testowej są zapisywane w pliku *UIMap.Designer.*

    > [!WARNING]
    > Po przeniesieniu metody nie będzie można edytować jej za pomocą Edytora kodowanego testu interfejsu użytkownika. Należy dodać niestandardowy kod i obsługiwać go za pomocą Edytora kodu.

10. Zmień nazwę metody `SimpleAppTest()` z do`ModifiedSimpleAppTest()`

11. Dodaj następującą instrukcję using do pliku:

    ```csharp
    using Microsoft.VisualStudio.TestTools.UITesting.WpfControls;
    ```

12. Dodaj następującą `WaitForControlEnabled()` metodę przed linią kodu naruszającą wcześniej zidentyfikowaną:

    ```csharp
    uICheckBoxCheckBox.WaitForControlEnabled();

    // Select 'CheckBox' check box
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;
    ```

13. W pliku *CodedUITest1.cs* zlokalizuj metodę **CodedUITestMethod** i skomentuj lub zmień nazwę odwołania do oryginalnej metody SimpleAppTest(), a następnie zastąp ją nową modifiedsimpleapptest():

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

14. W menu **Kompilacja** wybierz polecenie **Build Solution**.

15. Kliknij prawym przyciskiem myszy metodę **CodedUITestMethod** i wybierz polecenie **Uruchom testy**.

16. Tym razem zakodowany test interfejsu użytkownika pomyślnie kończy wszystkie kroki w teście, a **przekazany** jest wyświetlany w oknie **Eksploratora testów.**

## <a name="refactor-a-control-in-simplewpfapp"></a>Refaktoryzowanie formantu w SimpleWPFApp

1. W pliku *MainWindow.xaml* w projektancie wybierz kontrolkę przycisku.

2. W górnej części okna **Właściwości** zmień wartość właściwości **Nazwa** z **button1** na **buttonA**.

3. W menu **Kompilacja** wybierz polecenie **Build Solution**.

4. W **Eksploratorze testów**uruchom **codeduitestmethod1**.

     Test zakończy się niepowodzeniem, ponieważ w UIMap jako button1 kodowany test interfejsu użytkownika nie można znaleźć formantu przycisku, który pierwotnie był mapowany. Refaktoryzacja może w ten sposób wpłynąć na kodowane testy interfejsu użytkownika.

5. W **Eksploratorze testów**w sekcji **StackTrace** wybierz pierwsze łącze obok **pozycji UIMpa.ModifiedSimpleAppTest()**.

     Zostanie otwarty plik *UIMap.cs.* Punkt błędu jest wyróżniany w kodzie:

    ```csharp
    // Click 'Start' button
    Mouse.Click(uIStartButton, new Point(27, 10));
    ```

     Należy zauważyć, że wiersz kodu wcześniej `UiStartButton`w tej procedurze używa , który jest nazwą UIMap przed refaktoryzuje.

     Aby rozwiązać ten problem, można dodać refaktoryzowanego formantu do UIMap za pomocą **Coded UI Test Builder**. Można zaktualizować kod testu, aby użyć kodu, jak pokazano w następnej procedurze.

## <a name="map-refactored-control-rerun-the-test"></a>Kontrola refaktoryzowana mapa ponownie uruchomić test

1. W pliku *CodedUITest1.cs* w metodzie **CodedUITestMethod1()** wybierz polecenie **Generuj kod dla kodowany test interfejsu użytkownika,** a następnie wybierz polecenie **Użyj konstruktora kodowanych testów interfejsu użytkownika**.

     Pojawi **się kreator testów interfejsu użytkownika — kodowany.**

2. Korzystając ze skrótu pulpitu utworzonego wcześniej, uruchom aplikację SimpleWPFApp utworzoną wcześniej.

3. W oknie dialogowym **Kreator testów interfejsu użytkownika — kodowane** narzędzie do testowania interfejsu użytkownika przeciągnij narzędzie celownika do przycisku **Start** w aplikacji SimpleWPFApp.

     Przycisk **Start** jest ujęty w niebieskim pudełku. **Konstruktor kodowanych testów interfejsu użytkownika** trwa kilka sekund, aby przetworzyć dane dla wybranego formantu i wyświetlić właściwości formantu. Należy zauważyć, że wartość **AutomationUId** jest **buttonA**.

4. We właściwościach formantu wybierz strzałkę w lewym górnym rogu, aby rozwinąć Mapę formantów UI. Należy zauważyć, że **UIStartButton1** jest zaznaczona.

5. Na pasku narzędzi wybierz **pozycję Dodaj kontrolka do mapy sterowania interfejsami użytkownika**.

     Stan w dolnej części okna weryfikuje akcję, wyświetlając **wybrany formant został dodany do mapy sterowania interfejsu użytkownika**.

6. W oknie dialogowym **Konstruktora testów interfejsu użytkownika kodowany** wybierz pozycję **Generuj kod**.

     **Coded UI Test Builder — generowanie kodu** okno dialogowe pojawia się z notatką wskazującą, że nie jest wymagana żadna nowa metoda, a ten kod zostanie wygenerowany tylko dla zmian na mapie sterowania interfejsu użytkownika.

7. Wybierz **pozycję Generuj**.

8. Zamknij aplikację SimpleWPFApp.

9. Zamknij **UIMap - Kodowany konstruktor testów interfejsu użytkownika**.

10. W **Eksploratorze rozwiązań**otwórz plik *UIMap.Designer.cs.*

11. W pliku *UIMap.Designer.cs* zlokalizuj właściwość **UIStartButton1.** Zwróć `SearchProperties` uwagę, `"buttonA"`że jest ustawiona na:

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

     Teraz można zmodyfikować kodowany test interfejsu użytkownika do korzystania z ostatnio mapowanego formantu. Jak wskazano w poprzedniej procedurze, jeśli chcesz zastąpić wszelkie metody lub właściwości w kodowany test interfejsu użytkownika, należy to zrobić w *pliku UIMap.cs.*

12. W pliku *UIMap.cs* dodaj konstruktora i `SearchProperties` określ `UIStartButton` właściwość właściwości, aby użyć `AutomationID` właściwości o wartości`"buttonA":`

    ```csharp
    public UIMap()
            {
                this.UIMainWindowWindow.UIStartButton.SearchProperties[WpfButton.PropertyNames.AutomationId] = "buttonA";
            }
    ```

13. W menu **Kompilacja** wybierz polecenie **Build Solution**.

14. W **Eksploratorze testów**uruchom **codeduitestmethod1**.

     Tym razem kodowany test interfejsu użytkownika pomyślnie zakończy wszystkie etapy testu. W oknie **Wyniki testu** zostanie wyświetlony stan **Przekazany**.

## <a name="videos"></a>Filmy wideo

![łącze](../data-tools/media/playvideo.gif) do klipu wideo [Wprowadzenie do kodowanych testów interfejsu użytkownika](https://onedrive.live.com/?id=2DB0E1EFE1C1D3B8%21110&cid=2DB0E1EFE1C1D3B8)

## <a name="faq"></a>Często zadawane pytania

[Kodowane testy interfejsu użytkownika często zadawane pytania](https://social.msdn.microsoft.com/Forums/vsautotest/3a74dd2c-cef8-4923-abbf-7a91f489e6c4/faqs)

## <a name="see-also"></a>Zobacz też

- [Użyj automatyzacji interfejsu użytkownika, aby przetestować kod](../test/use-ui-automation-to-test-your-code.md)
- [Obsługiwane konfiguracje i platformy dla zakodowanych testów interfejsu użytkownika i nagrań akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [Edytowanie zakodowanych testów interfejsu użytkownika przy użyciu kodowego edytora testów interfejsu użytkownika](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)
