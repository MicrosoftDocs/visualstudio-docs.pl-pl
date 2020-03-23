---
title: Tworzenie dodatku dla podglądu wyników testów wydajności sieci Web
ms.date: 10/20/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, Visual Studio Add-in
- Visual Studio Add-in, Web performance tests
ms.assetid: 1118c604-4b1b-4b21-a04e-45995b676fa8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a6da2686a5a68325101e7161a51a8144e7ef42b6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589087"
---
# <a name="how-to-create-an-add-in-for-the-web-performance-test-results-viewer"></a>Jak: Tworzenie dodatku dla podglądu wyników testów wydajności sieci Web

Interfejs użytkownika przeglądarki wyników **testów wydajności sieci Web** można rozszerzyć przy użyciu następujących obszarów nazw:

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>

- <xref:Microsoft.VisualStudio.TestTools.WebTesting>

Ponadto należy dodać odwołanie do biblioteki DLL LoadTestPackage, która znajduje się w folderze *%ProgramFiles(x86)%\Microsoft Visual Studio\\\<>\Enterprise\Common7\IDE\PrivateAssemblies* folderu.

Aby rozszerzyć interfejs użytkownika **podglądu wyników testu wydajności sieci Web,** należy utworzyć dodatek programu Visual Studio i kontrolkę użytkownika. Poniższe procedury wyjaśniają, jak utworzyć dodatek, formant użytkownika i jak zaimplementować klasy niezbędne do rozszerzenia interfejsu użytkownika **podglądu wyników testu wydajności sieci Web.**

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="create-or-open-a-solution-that-contains-an-aspnet-web-application-and-a-web-performance-and-load-test-project"></a>Tworzenie lub otwieranie rozwiązania zawierającego ASP.NET aplikacji sieci web oraz projektu testu wydajności i obciążenia sieci Web

### <a name="to-prepare-for-extending-the-web-performance-test-results-viewer"></a>Aby przygotować się do rozszerzenia podglądu wyników testów wydajności sieci Web

Utwórz lub otwórz rozwiązanie nieprodukcyjne, z którym można eksperymentować, z którym zawiera ASP.NET aplikacji sieci web i projektu testu wydajności sieci web i obciążenia z co najmniej jednym testem wydajności sieci web dla ASP.NET aplikacji sieci web.

> [!NOTE]
> Można utworzyć ASP.NET aplikacji sieci web i projektu testu wydajności sieci web i obciążenia, który zawiera testy wydajności sieci web, wykonując procedury w [jak: Tworzenie testu usługi sieci web](../test/how-to-create-a-web-service-test.md) i [generowanie i uruchamianie zakodowany test wydajności sieci Web](../test/generate-and-run-a-coded-web-performance-test.md).

## <a name="create-a-visual-studio-add-in"></a>Tworzenie dodatku programu Visual Studio

Dodatek jest skompilowaną biblioteką DLL, która jest uruchamiana w zintegrowanym środowisku programistycznym Programu Visual Studio (IDE). Kompilacja pomaga chronić własność intelektualną i poprawia wydajność. Chociaż dodatki można tworzyć ręcznie, korzystanie z **Kreatora dodatków**może być łatwiejsze. Ten kreator tworzy funkcjonalny, ale podstawowy dodatek, który można uruchomić natychmiast po jego utworzeniu. Po wygenerowaniu przez **Kreatora dodatków** podstawowy program można dodać do niego kod i dostosować go.

**Kreator dodatków** umożliwia podanie nazwy wyświetlanej i opisu dodatku. Oba pojawią się w **Menedżerze dodatków**. Opcjonalnie kreator może wygenerować kod, który dodaje do menu **Narzędzia** polecenie, aby otworzyć dodatek. Można również wyświetlić niestandardowe okno dialogowe **Informacje** dla dodatku. Po zakończeniu pracy kreatora, masz nowy projekt, który ma tylko jedną klasę, która implementuje dodatek. Ta klasa nosi nazwę Connect.

Menedżer **dodatków** użyje na końcu tego artykułu.

### <a name="to-create-an-add-in-by-using-the-add-in-wizard"></a>Aby utworzyć dodatek za pomocą Kreatora dodatków

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy rozwiązanie, wybierz polecenie **Dodaj**, a następnie wybierz pozycję **Nowy projekt**.

2. Utwórz nowy projekt **dodatku programu Visual Studio.**

    Uruchamia się **Kreator dodatków** programu Visual Studio.

3. Wybierz pozycję **Dalej**.

4. Na stronie **Wybierz język programowania** wybierz język programowania, którego chcesz użyć do zapisania dodatku.

   > [!NOTE]
   > W tym temacie użyto języka Visual C# dla przykładowego kodu.

5. Na stronie **Wybierz hosta aplikacji** wybierz pozycję **Visual Studio** i **wyczyść wyczyść makra programu Visual Studio**.

6. Wybierz pozycję **Dalej**.

7. Wpisz nazwę i opis dodatku na stronie **Wprowadź nazwę i opis.**

     Po utworzeniu dodatku jego nazwa i opis są wyświetlane na liście Dostępne dodatki w **Menedżerze** **dodatków** . Dodaj wystarczająco dużo szczegółów do opisu dodatku, aby użytkownicy mogli dowiedzieć się, co robi dodatek, jak działa i tak dalej.

8. Wybierz pozycję **Dalej**.

9. Na stronie **Wybieranie opcji dodatku** wybierz pozycję **Chciałbym, aby mój dodatek był ładowany po uruchomieniu aplikacji hosta.**

10. Wyczyść pozostałe pola wyboru.

11. Na stronie **Wybieranie informacji o pomocy** można określić, czy informacje o dodatku mają być wyświetlane w oknie dialogowym **Informacje.** Jeśli chcesz, aby informacje były wyświetlane, zaznacz pole **wyboru Tak, chcę, aby mój dodatek oferował informacje "Informacje o".**

     Informacje, które można dodać do okna dialogowego **Informacje programu** Visual Studio obejmują numer wersji, szczegóły pomocy technicznej, dane licencyjne i tak dalej.

12. Wybierz pozycję **Dalej**.

13. Wybrane opcje są wyświetlane na stronie **Podsumowanie,** aby można było ją przejrzeć. Jeśli jesteś zadowolony, wybierz **zakończ,** aby utworzyć dodatek. Jeśli chcesz coś zmienić, wybierz przycisk **Wstecz.**

     Nowe rozwiązanie i projekt są tworzone, a plik *Connect.cs* dla nowego dodatku jest wyświetlany w **Edytorze kodu**.

     Do pliku *Connect.cs* zostanie dodana po poniższej procedurze, która tworzy formant użytkownika, do którego odwołuje się ten projekt WebPerfTestResultsViewerAddin.

    Po utworzeniu dodatku należy zarejestrować go w programie Visual Studio, aby można go było aktywować w **Menedżerze dodatków**. Można to zrobić za pomocą pliku XML, który ma rozszerzenie nazwy pliku *.addin.*

    Plik *.addin* opisuje informacje, których program Visual Studio wymaga do wyświetlania dodatku w **Menedżerze dodatków**. Po uruchomieniu programu Visual Studio wyszukuje w lokalizacji pliku *.addin* wszystkie dostępne pliki *.addin.* Jeśli znajdzie jakiekolwiek, odczytuje plik XML i daje **Add-In Manager** informacje, które wymaga, aby uruchomić dodatek po kliknięciu.

    Plik *.addin* jest tworzony automatycznie podczas tworzenia dodatku za pomocą **Kreatora dodatków**.

### <a name="add-in-file-locations"></a>Lokalizacje plików dodatków

Dwie kopie plików *.addin* są tworzone automatycznie przez **Kreatora dodatków w**następujący sposób:

|**. Lokalizacja pliku addin**|**Opis**|
|-|----------------------------|-|
|Główny folder projektu|Używane do wdrażania projektu dodatku. Zawarte w projekcie dla ułatwienia edycji i ma ścieżkę lokalną dla xcopy stylu wdrożenia.|
|Folder dodatku|Służy do uruchamiania dodatku w środowisku debugowania. Zawsze należy wskazać ścieżkę wyjściową bieżącej konfiguracji kompilacji.|

## <a name="create-a-windows-form-control-library-project"></a>Tworzenie projektu biblioteki kontroli formularzy systemu Windows

Dodatek Visual Studio utworzony w poprzedniej procedurze odwołuje się do projektu Biblioteki <xref:System.Windows.Forms.UserControl> kontroli formularzy systemu Windows w celu utworzenia wystąpienia klasy.

### <a name="to-create-a-control-to-be-used-in-the-web-test-results-viewer"></a>Aby utworzyć formant do użycia w przeglądarce wyników testów sieci Web

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy rozwiązanie, wybierz polecenie **Dodaj**, a następnie wybierz pozycję **Nowy projekt**.

2. Utwórz nowy projekt **biblioteki kontroli formularzy systemu Windows.**

3. Z **przybornika**przeciągnij a <xref:System.Windows.Forms.DataGridView> na powierzchnię userControl1.

4. Kliknij glif znacznika![akcji (Smart](../test/media/vs_winformsmttagglyph.gif)Tag Glyph) w <xref:System.Windows.Forms.DataGridView> prawym górnym rogu i wykonaj następujące kroki:

    1. Wybierz **pozycję Dok w kontenerze nadrzędnym**.

    2. Wyczyść pola wyboru **Włącz dodawanie,** **Włącz edycję**, **Włącz usuwanie** i Włącz ponowne **ustawienie kolumny**.

    3. Wybierz **pozycję Dodaj kolumnę**.

         Zostanie wyświetlone okno dialogowe **Dodawanie kolumny.**

    4. Z listy rozwijanej **Typ** wybierz pozycję **DataGridViewTextBoxColumn**.

    5. Wyczyść tekst "Kolumna1" w **tekście nagłówka**.

    6. Wybierz **pozycję Dodaj**.

    7. Wybierz **pozycję Zamknij**.

5. W oknie **Właściwości** zmień właściwość <xref:System.Windows.Forms.DataGridView> **(Nazwa)** **do resultControlDataGridView**.

6. Kliknij prawym przyciskiem myszy powierzchnię projektową i wybierz polecenie **Wyświetl kod**.

     Plik *UserControl1.cs* jest wyświetlany w **Edytorze kodu**.

7. Zmień nazwę <xref:System.Windows.Forms.UserControl> klasy wystąpienia z UserContro1 na resultControl:

    ```csharp
    namespace WebPerfTestResultsViewerControl
    {
        public partial class resultControl : UserControl
        {
            public resultControl()
            {
                InitializeComponent();
            }
    ```

     W następnej procedurze dodasz kod do pliku *Connect.cs* projektu WebPerfTestResultsViewerAddin, który będzie odwoływał się do klasy resultControl.

     Później do pliku *Connect.cs* dodasz dodatkowy kod.

## <a name="add-code-to-the-webperftestresultsvieweraddin"></a>Dodaj kod do WebPerfTestResultsViewerAddin

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł **Odwołania** w projekcie WebPerfTestResultsViewerAddin i wybierz polecenie **Dodaj odwołanie**.

2. W oknie dialogowym **Dodawanie odwołania** wybierz kartę **.NET.**

3. Przewiń w dół i wybierz pozycję **Microsoft.VisualStudio.QualityTools.WebTestFramework** i **System.Windows.Forms**.

4. Wybierz pozycję **OK**.

5. Ponownie kliknij prawym przyciskiem myszy węzeł **Odwołania,** a następnie wybierz polecenie **Dodaj odwołanie**.

6. W oknie dialogowym **Dodawanie odwołania** wybierz kartę **Przeglądaj.**

7. Wybierz pozycję rozwijaną **Funkcji Szukaj** i przejdź do *pozycji %ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies* i wybierz plik *Microsoft.VisualStudio.QualityTools.LoadTestPackage.dll.*

8. Wybierz pozycję **OK**.

9. Kliknij prawym przyciskiem myszy węzeł projektu WebPerfTestResultsViewerAddin, a następnie wybierz polecenie **Dodaj odwołanie**.

10. W oknie dialogowym **Dodawanie odwołania** wybierz kartę **Projekty.**

11. W obszarze **Nazwa projektu**wybierz projekt **WebPerfTestResultsViewerControl** i wybierz przycisk **OK**.

12. Jeśli plik *Connect.cs* nie jest nadal otwarty, w **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy plik **Connect.cs** w projekcie WebPerfTestResultsViewerAddin i wybierz polecenie **Wyświetl kod**.

13. W pliku *Connect.cs* dodaj następujące instrukcje Using:

    ```csharp
    using System.IO;
    using System.Windows.Forms;
    using System.Collections.Generic;
    using Microsoft.VisualStudio.TestTools.LoadTesting;
    using Microsoft.VisualStudio.TestTools.WebTesting;
    using WebPerfTestResultsViewerControl;
    ```

14. Przewiń w dół do dołu *Connect.cs* pliku. Należy dodać listę identyfikatorów GUID <xref:System.Windows.Forms.UserControl> dla w przypadku, gdy więcej niż jedno wystąpienie **podglądu wyników testów wydajności sieci Web** jest otwarty. Później dodasz kod, który używa tej listy.

     Druga lista ciągów jest używana w OnDiscconection metody, które zostaną zakodowane później.

    ```csharp
    private DTE2 _applicationObject;
    private AddIn _addInInstance;

    private Dictionary<Guid, List<UserControl>> m_controls = new Dictionary<Guid, List<UserControl>>();        private List<string> temporaryFilePaths = new List<string>();
    ```

15. Plik *Connect.cs* wystąpienia klasy o nazwie Połącz <xref:Extensibility.IDTExtensibility2> z klasy, a także zawiera niektóre metody implementacji dodatku programu Visual Studio. Jedną z metod jest OnConnection metoda, która odbiera powiadomienie, że dodatek jest ładowany. W OnConnection metody użyjesz LoadTestPackageExt klasy do utworzenia pakietu rozszerzalności dla **przeglądarki wyników testu wydajności sieci Web**. Dodaj następujący kod do metody OnConnection:

    ```csharp
    public void OnConnection(object application, ext_ConnectMode connectMode, object addInInst, ref Array custom)
                {
                _applicationObject = (DTE2)application;
                _addInInstance = (AddIn)addInInst;

                // Create a load test packge extensibility class.            LoadTestPackageExt loadTestPackageExt = _applicationObject.GetObject("Microsoft.VisualStudio.TestTools.LoadTesting.LoadTestPackageExt") as LoadTestPackageExt;            // Process open windows.            foreach (WebTestResultViewer webTestResultViewer in loadTestPackageExt.WebTestResultViewerExt.ResultWindows)            {                WindowCreated(webTestResultViewer);            }            // Create event handlers.            loadTestPackageExt.WebTestResultViewerExt.WindowCreated += new EventHandler<WebTestResultViewerExt.WindowCreatedEventArgs>(WebTestResultViewerExt_WindowCreated);            loadTestPackageExt.WebTestResultViewerExt.WindowClosed += new EventHandler<WebTestResultViewerExt.WindowClosedEventArgs>(WebTesResultViewer_WindowClosed);            loadTestPackageExt.WebTestResultViewerExt.SelectionChanged += new EventHandler<WebTestResultViewerExt.SelectionChangedEventArgs>(WebTestResultViewer_SelectedChanged);
            }
    ```

16. Dodaj następujący kod do klasy connect, aby utworzyć metodę WebTestResultViewerExt_WindowCreated dla loadTestPackageExt.WebTestResultViewerExt.WindowCreated obsługi zdarzeń, który został dodany w OnConnection metody i WindowCreated metody, która wywołanie metody WebTestResultViewerExt_WindowCreated.

    ```csharp
            void WebTestResultViewerExt_WindowCreated(object sender, WebTestResultViewerExt.WindowCreatedEventArgs e)
            {
                // New control added to new result viewer window.
                WindowCreated(e.WebTestResultViewer);
            }

    private void WindowCreated(WebTestResultViewer viewer)        {            // Instantiate an instance of the resultControl referenced in the WebPerfTestResultsViewerControl project.
                resultControl resultControl = new resultControl();            // Add to the dictionary of open playback windows.            System.Diagnostics.Debug.Assert(!m_controls.ContainsKey(viewer.TestResultId));            List<UserControl> userControls = new List<UserControl>();            userControls.Add(resultControl);            // Add Guid to the m_control List to manage Result viewers and controls.            m_controls.Add(viewer.TestResultId, userControls);            // Add tabs to the playback control.            resultControl.Dock = DockStyle.Fill;            viewer.AddResultPage(new Guid(), "Sample", resultControl);        }
    ```

17. Dodaj następujący kod do klasy connect, aby utworzyć metodę WebTestResultViewer_SelectedChanged dla loadTestPackageExt.WebTestResultViewerExt.SelectionChanged obsługi zdarzeń, który został dodany w OnConnection metody:

    ```csharp
    void WebTestResultViewer_SelectedChanged(object sender, WebTestResultViewerExt.SelectionChangedEventArgs e)
    {
        foreach (UserControl userControl in m_controls[e.TestResultId])            {                // Update the userControl in each result viewer.                resultControl resultControl = userControl as resultControl;                if (resultControl != null)                    // Call the resultControl's Update method (This will be added in the next procedure).                    resultControl.Update(e.WebTestRequestResult);            }
    }
    ```

18. Dodaj następujący kod do klasy connect, aby utworzyć metodę WebTesResultViewer_WindowClosed dla programu obsługi zdarzeń dla loadTestPackageExt.WebTestResultViewerExt.WindowClosedtwo dodane w metodzie OnConnection:

    ```csharp
    void WebTesResultViewer_WindowClosed(object sender, WebTestResultViewerExt.WindowClosedEventArgs e)
    {
        if (m_controls.ContainsKey(e.WebTestResultViewer.TestResultId))
        {
            m_controls.Remove(e.WebTestResultViewer.TestResultId);
        }
    }
    ```

     Teraz, gdy kod został ukończony dla dodatku Visual Studio, należy dodać Update metody do resultControl w projekcie WebPerfTestResultsViewerControl.

## <a name="add-code-to-the-webperftestresultsviewercontrol"></a>Dodawanie kodu do kontrolera WebPerfTestResultsViewerControl

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu WebPerfTestResultsViewerControl i wybierz polecenie **Właściwości**.

2. Wybierz kartę **Aplikacja,** a następnie wybierz listę rozwijaną **Struktura docelowa** i wybierz pozycję **.NET Framework 4** (lub nowszą). Zamknij okno **Właściwości.**

   Jest to wymagane do obsługi odwołań do biblioteki DLL, które są potrzebne do rozszerzenia **podglądu wyników testów wydajności sieci Web.**

3. W **Eksploratorze rozwiązań**w projekcie WebPerfTestResultsViewerControl kliknij prawym przyciskiem myszy węzeł **Odwołania** i wybierz polecenie **Dodaj odwołanie**.

4. W oknie dialogowym **Dodawanie odwołania** kliknij kartę **.NET.**

5. Przewiń w dół i wybierz pozycję **Microsoft.VisualStudio.QualityTools.WebTestFramework**.

6. Wybierz pozycję **OK**.

7. W pliku *UserControl1.cs* dodaj następujące instrukcje Using:

    ```csharp
    using Microsoft.VisualStudio.TestTools.WebTesting;
    using Microsoft.VisualStudio.TestTools.WebTesting.Rules;
    ```

8. Dodaj Update metoda, która jest wywoływana i przekazywane WebTestRequestResult z WebPerfTestResultsViewerAddin WebTestResultViewer_SelectedChanged metody w pliku *Connect.cs.* Update Metoda wypełnia DataGridView z różnych właściwości przekazanych do niego w WebTestRequestResult.

    ```csharp
    public void Update(WebTestRequestResult WebTestResults)
            {
                // Clear the DataGridView when a request is selected.
                resultControlDataGridView.Rows.Clear();
                // Populate the DataGridControl with properties from the WebTestResults.
                this.resultControlDataGridView.Rows.Add("Request: " + WebTestResults.Request.Url.ToString());
                this.resultControlDataGridView.Rows.Add("Response: " + WebTestResults.Response.ResponseUri.ToString());
                foreach (RuleResult ruleResult in WebTestResults.ExtractionRuleResults)
                {
                    this.resultControlDataGridView.Rows.Add("Extraction rule results: " + ruleResult.Message.ToString());
                }
                foreach (RuleResult ruleResult in WebTestResults.ValidationRuleResults)
                {
                    this.resultControlDataGridView.Rows.Add("Validation rule results: " + ruleResult.Message.ToString());
                }
                foreach (WebTestError webTestError in WebTestResults.Errors)
                {
                    this.resultControlDataGridView.Rows.Add("Error: " + webTestError.ErrorType.ToString() + " " + webTestError.ErrorSubtype.ToString() + " " + webTestError.ExceptionText.ToString());
                }
            }
    ```

## <a name="build-the-solution"></a>Kompilowanie rozwiązania

- W menu **Kompilacja** wybierz polecenie **Buduj rozwiązanie**.

## <a name="register-the-webperftestresultsvieweraddin-add-in"></a>Zarejestruj dodatek WebPerfTestResultsViewerAddin

1. W menu **Narzędzia** wybierz polecenie **Menedżer dodatków**.

2. Zostanie wyświetlone okno dialogowe **Menedżer dodatków.**

3. Zaznacz pole wyboru dodatku WebPerfTestResultsViewerAddin w kolumnie Dostępne dodatki i **wyczyść** pola wyboru pod kolumnami **Uruchamianie** i **Wiersz polecenia.**

4. Wybierz pozycję **OK**.

## <a name="run-the-web-performance-test-using-the-web-test-results-viewer"></a>Uruchamianie testu wydajności sieci Web przy użyciu przeglądarki wyników testów sieci Web

1. Uruchom test wydajności sieci Web, a zobaczysz nową kartę dodatku WebPerfTestResultsViewerAddin zatytułowaną Przykład wyświetlany w **przeglądarce wyników testów wydajności sieci Web**.

2. Wybierz kartę, aby wyświetlić właściwości prezentowane w datagridview.

## <a name="net-security"></a>Zabezpieczenia platformy .NET

Aby zwiększyć bezpieczeństwo, zapobiegając automatycznemu aktywowaniu złośliwych dodatków, program Visual Studio udostępnia ustawienia na stronie **Opcje narzędzi** o nazwie **Add-in/Macros Security**.

Ponadto ta strona opcji umożliwia określenie folderów, w których program Visual Studio wyszukuje *program . Pliki rejestracyjne AddIn.* Zwiększa to bezpieczeństwo, umożliwiając ograniczenie lokalizacji, w których *. Pliki rejestracyjne AddIn* można odczytać. Pomaga to zapobiegać złośliwemu *programowi . AddIn* plików z nieumyślnie używane.

**Ustawienia zabezpieczeń dodatku**

Ustawienia na stronie opcji zabezpieczeń dodatku są następujące:

- **Zezwalaj na ładowanie składników dodatku.** Domyślnie zaznaczony. Gdy ta opcja jest zaznaczona, dodatki mogą być ładowane w programie Visual Studio. Jeśli nie jest zaznaczona, dodatki nie mogą ładować w programie Visual Studio.

- **Zezwalaj na ładowanie składników dodatku z adresu URL.** Nie jest zaznaczona domyślnie. Po wybraniu tej opcji dodatki można ładować z zewnętrznych witryn sieci Web. Jeśli nie jest zaznaczona, zdalne dodatki nie mogą ładować się w programie Visual Studio. Jeśli dodatek nie może załadować z jakiegoś powodu, nie można go załadować z sieci Web. To ustawienie steruje tylko ładowaniem biblioteki DLL dodatku. W *. Pliki rejestracyjne dodatków* muszą zawsze znajdować się w systemie lokalnym.

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.UserControl>
- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules>
- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.DataGrid>
- [Tworzenie niestandardowych kodów i wtyczek dla testów obciążeniowych](../test/create-custom-code-and-plug-ins-for-load-tests.md)
