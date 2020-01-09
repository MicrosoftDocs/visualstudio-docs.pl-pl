---
title: Tworzenie dodatku dla podglądu wyników testu wydajności sieci Web
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589087"
---
# <a name="how-to-create-an-add-in-for-the-web-performance-test-results-viewer"></a>Instrukcje: Tworzenie dodatku dla usługi Web Performance Wyniki testów Viewer

Możesz rozszerzyć w interfejsie użytkownika dla **podglądu wyników testu wydajności sieci Web** przy użyciu następujących przestrzeni nazw:

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>

- <xref:Microsoft.VisualStudio.TestTools.WebTesting>

Ponadto należy dodać odwołanie do biblioteki DLL LoadTestPackage, która znajduje się w folderze *% ProgramFiles (x86)% \ Microsoft Visual Studio\\\<wersja > \Enterprise\Common7\IDE\PrivateAssemblies* .

Aby rozszerzyć **podglądu wyników testu wydajności sieci Web**w interfejsie użytkownika, należy utworzyć dodatek programu Visual Studio i kontrolki użytkownika. W poniższych procedurach opisano sposób tworzenia dodatku, formantu użytkownika oraz sposób implementacji klas niezbędnych do rozszerzenia **podglądu wyników testu wydajności sieci Web**w interfejsie użytkownika.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="create-or-open-a-solution-that-contains-an-aspnet-web-application-and-a-web-performance-and-load-test-project"></a>Utwórz lub Otwórz rozwiązanie, które zawiera projekt testu wydajności i obciążenia sieci web i aplikacji sieci web ASP.NET

### <a name="to-prepare-for-extending-the-web-performance-test-results-viewer"></a>Aby przygotować się do rozszerzania podglądu wyników testu wydajności sieci Web

Utwórz lub Otwórz rozwiązanie spoza środowiska produkcyjnego, że możesz eksperymentować z zawierającego aplikację sieci web platformy ASP.NET i wydajności sieci web i obciążenia projektu testowego z jednego lub więcej testów wydajności sieci web dla aplikacji sieci web platformy ASP.NET.

> [!NOTE]
> Możesz utworzyć aplikację sieci web platformy ASP.NET i projekt zawierający testy wydajności sieci web zgodnie z instrukcjami opisanymi w testu wydajności sieci web i obciążenia [porady: Tworzenie nowego testu usługi internetowej](../test/how-to-create-a-web-service-test.md) i [Generowanie i uruchom kodowany internetowy test wydajności](../test/generate-and-run-a-coded-web-performance-test.md).

## <a name="create-a-visual-studio-add-in"></a>Utwórz dodatek programu Visual Studio

Dodatek jest skompilowaną biblioteką DLL, która działa w programie Visual Studio zintegrowane środowisko programistyczne (IDE). Kompilacja pomaga chronić Twoje prawa własności intelektualnej i zwiększa wydajność. Chociaż dodatki można utworzyć ręcznie, może okazać się łatwiejszy w obsłudze **kreatora dodatków**. Ten kreator tworzy funkcjonalny, ale podstawowy dodatek, którą można uruchamiać natychmiast po utworzeniu. Po **kreatora dodatków** wygeneruje podstawowy program, można dodać do niego kod i go dostosować.

**Kreatora dodatków** pozwala podać nazwę wyświetlaną i opis dla dodatku. Obie subskrypcje będą widoczne w **Add-In Manager**. Opcjonalnie może mieć kod Generuj kreatora, który dodaje do **narzędzia** menu polecenie, aby otworzyć dodatek. Możesz również wyświetlić niestandardowe **o** okno dialogowe dla dodatku. Po zakończeniu działania kreatora, masz nowy projekt, który ma tylko jedną klasę, która implementuje dodatek. Ta klasa ma nazwę Połącz.

Użyjesz **Add-In Manager** na końcu tego artykułu.

### <a name="to-create-an-add-in-by-using-the-add-in-wizard"></a>Aby utworzyć dodatek za pomocą Kreatora dodatek

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie, wybierz pozycję **Dodaj**, a następnie wybierz pozycję **nowy projekt**.

2. Utwórz nowy projekt **dodatku programu Visual Studio** .

    Visual Studio **kreatora dodatków** rozpoczyna się.

3. Wybierz **dalej**.

4. Na **wybierz język programowania** wybierz język programowania, który chcesz użyć do pisania dodatku.

   > [!NOTE]
   > Ten temat używa języka Visual C# dla przykładowego kodu.

5. Na **wybierz aplikację hosta** wybierz **programu Visual Studio** i wyczyść **makra programu Visual Studio**.

6. Wybierz **dalej**.

7. Wpisz nazwę i opis dla dodatku na **wprowadź nazwę i opis** strony.

     Gdy dodatek zostanie utworzona, jego nazwa i opis są wyświetlane w **dostępne dodatki** listy w **Add-In Manager**. Dodaj tyle szczegółowy opis dodatku, dzięki czemu użytkownicy mogą dowiedzieć się, jakie dodatku nie, jak działa i tak dalej.

8. Wybierz **dalej**.

9. Na **wybierz opcje dodatku** wybierz opcję **chciałbym aby dodatek załadowany gdy uruchomiona zostanie aplikacja hosta**.

10. Wyczyść pozostałe pola wyboru.

11. Na **wybór informacji "Pomoc na temat"** strony, należy można określić, czy informacje o dodatku mają być wyświetlane w **o** okno dialogowe. Jeśli chcesz, aby informacje były wyświetlane, zaznacz **tak, chciałbym aby dodatek zawierał okno informacji "o"** pole wyboru.

     Informacje, które mogą być dodawane do programu Visual Studio **o** okno dialogowe zawiera numer wersji, szczegóły pomocy technicznej, dane licencyjne i tak dalej.

12. Wybierz **dalej**.

13. Wybrane opcje są wyświetlane na **Podsumowanie** stron, którymi możesz się zapoznać. Jeśli Cię zadowala, wybierz opcję **Zakończ** do utworzenia dodatku. Jeśli chcesz coś zmienić, wybierz opcję **ponownie** przycisku.

     Nowe rozwiązanie i projekt są tworzone i *Connect.cs* plików dla nowych dodatków jest wyświetlany w **Edytor kodu**.

     Możesz dodać kod, aby *Connect.cs* plik po poniższej procedury, która tworzy kontrolkę użytkownika, który będzie się odnosić projekt WebPerfTestResultsViewerAddin.

    Gdy dodatek zostanie utworzona, należy zarejestrować go za pomocą programu Visual Studio można ją aktywować na **Add-In Manager**. Możesz to zrobić przy użyciu pliku XML, który ma *.addin* rozszerzenie nazwy pliku.

    *.Addin* pliku w tym artykule opisano informacje, które wymaga programu Visual Studio, aby wyświetlić dodatek w **Add-In Manager**. Po uruchomieniu programu Visual Studio szuka w *.addin* lokalizacji dla każdego pliku dostępne *.addin* plików. Jeśli jakiekolwiek znajdzie, odczytuje plik XML i daje **Add-In Manager** informacje, które ten wymaga do uruchomienia dodatku po kliknięciu.

    *.Addin* pliku jest tworzony automatycznie podczas tworzenia dodatku za pomocą **kreatora dodatków**.

### <a name="add-in-file-locations"></a>Lokalizacje pliku dodatku

Dwie kopie *.addin* pliki są tworzone automatycznie przez **kreatora dodatków**, wykonując następujące czynności:

|**. Lokalizacja pliku dodatku**|**Opis**|
|-|----------------------------|-|
|Głównego folderu projektu|Używany do wdrażania projektu dodatek. Uwzględnione w projekcie w celu ułatwienia edycji i ma ścieżkę lokalną dla wdrażania w formacie xcopy.|
|Folder dodatków|Używane do uruchamiania dodatku w środowisku debugowania. Zawsze powinien wskazywać ścieżkę wyjściową bieżącej konfiguracji kompilacji.|

## <a name="create-a-windows-form-control-library-project"></a>Utwórz projekt Biblioteka kontrolek formularzy Windows

Visual Studio dodatek utworzony w poprzedniej procedurze odwołuje się do projektu Biblioteka kontrolek formularzy Windows, aby utworzyć wystąpienie <xref:System.Windows.Forms.UserControl> klasy.

### <a name="to-create-a-control-to-be-used-in-the-web-test-results-viewer"></a>Aby utworzyć formant ma być używany w podglądzie wyników testu sieci Web

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie, wybierz pozycję **Dodaj**, a następnie wybierz pozycję **nowy projekt**.

2. Utwórz nowy projekt **biblioteki formantów Windows Forms** .

3. Z **przybornika**, przeciągnij <xref:System.Windows.Forms.DataGridView> na powierzchnię obiektu userControl1.

4. Kliknij symbol tagu akcji (![symbol tagu inteligentnego](../test/media/vs_winformsmttagglyph.gif)) w prawym górnym rogu <xref:System.Windows.Forms.DataGridView> i wykonaj następujące czynności:

    1. Wybierz **Zadokuj w kontenerze nadrzędnym**.

    2. Usuń zaznaczenie pól wyboru dla **Włącz dodawanie**, **Włącz edytowanie**, **Włącz usuwanie** i **Włącz zmienianie kolejności kolumn**.

    3. Wybierz **Dodaj kolumnę**.

         **Dodaj kolumnę** zostanie wyświetlone okno dialogowe.

    4. W **typu** listy rozwijanej wybierz **DataGridViewTextBoxColumn**.

    5. Wyczyść tekst "Kolumna1" w **tekst nagłówka**.

    6. Wybierz **Dodaj**.

    7. Wybierz **Zamknij**.

5. W **właściwości** oknie zmiany **(nazwa)** właściwość <xref:System.Windows.Forms.DataGridView> do **resultControlDataGridView**.

6. Kliknij prawym przyciskiem myszy projekt powierzchni i wybierz **Wyświetl kod**.

     *UserControl1.cs* plik jest wyświetlany w **Edytor kodu**.

7. Zmień nazwę skonkretyzowanej <xref:System.Windows.Forms.UserControl> klasy z UserContro1 na resultControl:

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

     W następnej procedurze, dodasz kod do projektu WebPerfTestResultsViewerAddin *Connect.cs* pliku, który będzie odwoływać się do klasy resultControl.

     Będziesz dodawać dodatkowy kod w celu *Connect.cs* pliku później.

## <a name="add-code-to-the-webperftestresultsvieweraddin"></a>Dodaj kod do dodatku WebPerfTestResultsViewerAddin

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** węzeł w projekcie WebPerfTestResultsViewerAddin i wybierz pozycję **Dodaj odwołanie**.

2. W **Dodaj odwołanie** okna dialogowego wybierz **.NET** kartę.

3. Przewiń w dół i wybierz **Microsoft.VisualStudio.QualityTools.WebTestFramework** i **System.Windows.Forms**.

4. Wybierz **OK**.

5. Kliknij prawym przyciskiem myszy **odwołania** ponownie, a następnie wybierz węzeł **Dodaj odwołanie**.

6. W **Dodaj odwołanie** okna dialogowego wybierz **Przeglądaj** kartę.

7. Wybierz listę rozwijaną dla **przeszukania** i przejdź do *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies* i wybierz  *Microsoft.VisualStudio.QualityTools.LoadTestPackage.dll* pliku.

8. Wybierz **OK**.

9. Kliknij prawym przyciskiem myszy węzeł projektu WebPerfTestResultsViewerAddin i wybierz **Dodaj odwołanie**.

10. W **Dodaj odwołanie** okna dialogowego wybierz **projektów** kartę.

11. W obszarze **Nazwa projektu**, wybierz opcję **WebPerfTestResultsViewerControl** projektu, a następnie wybierz **OK**.

12. Jeśli *Connect.cs* plik nie jest wciąż otwarty, w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Connect.cs** plik w projekcie WebPerfTestResultsViewerAddin i wybierz  **Wyświetlanie kodu**.

13. W *Connect.cs* Dodaj następujące instrukcje Using:

    ```csharp
    using System.IO;
    using System.Windows.Forms;
    using System.Collections.Generic;
    using Microsoft.VisualStudio.TestTools.LoadTesting;
    using Microsoft.VisualStudio.TestTools.WebTesting;
    using WebPerfTestResultsViewerControl;
    ```

14. Przewiń w dół do dolnej części *Connect.cs* pliku. Musisz dodać listę identyfikatorów GUID dla <xref:System.Windows.Forms.UserControl> w przypadku więcej niż jedno wystąpienie **podglądu wyników testu wydajności sieci Web** jest otwarty. Należy dodać później kod, który używa tej listy.

     Druga lista ciągu jest używany w metodzie OnDiscconection, która będzie kodowana później.

    ```csharp
    private DTE2 _applicationObject;
    private AddIn _addInInstance;

    private Dictionary<Guid, List<UserControl>> m_controls = new Dictionary<Guid, List<UserControl>>();        private List<string> temporaryFilePaths = new List<string>();
    ```

15. *Connect.cs* pliku tworzy wystąpienia klasy o nazwie Połącz z <xref:Extensibility.IDTExtensibility2> klasy i zawiera także kilka metod wykonania dodatku programu Visual Studio. Jedną z metod jest metodą OnConnection, które otrzymuje powiadomienie, że dodatek jest ładowany. W metodzie OnConnection użyjesz klasy LoadTestPackageExt do utworzenia pakietu rozszerzeń dla **podglądu wyników testu wydajności sieci Web**. Dodaj następujący kod do metody OnConnection:

    ```csharp
    public void OnConnection(object application, ext_ConnectMode connectMode, object addInInst, ref Array custom)
                {
                _applicationObject = (DTE2)application;
                _addInInstance = (AddIn)addInInst;

                // Create a load test packge extensibility class.            LoadTestPackageExt loadTestPackageExt = _applicationObject.GetObject("Microsoft.VisualStudio.TestTools.LoadTesting.LoadTestPackageExt") as LoadTestPackageExt;            // Process open windows.            foreach (WebTestResultViewer webTestResultViewer in loadTestPackageExt.WebTestResultViewerExt.ResultWindows)            {                WindowCreated(webTestResultViewer);            }            // Create event handlers.            loadTestPackageExt.WebTestResultViewerExt.WindowCreated += new EventHandler<WebTestResultViewerExt.WindowCreatedEventArgs>(WebTestResultViewerExt_WindowCreated);            loadTestPackageExt.WebTestResultViewerExt.WindowClosed += new EventHandler<WebTestResultViewerExt.WindowClosedEventArgs>(WebTesResultViewer_WindowClosed);            loadTestPackageExt.WebTestResultViewerExt.SelectionChanged += new EventHandler<WebTestResultViewerExt.SelectionChangedEventArgs>(WebTestResultViewer_SelectedChanged);
            }
    ```

16. Dodaj następujący kod do klasy Połącz, aby utworzyć metodę WebTestResultViewerExt_WindowCreated dla programu obsługi zdarzeń loadtestpackageext.webtestresultviewerext.windowcreated, które zostały dodane w metodzie OnConnection i metodę WindowCreated, wywołuje metodę WebTestResultViewerExt_WindowCreated.

    ```csharp
            void WebTestResultViewerExt_WindowCreated(object sender, WebTestResultViewerExt.WindowCreatedEventArgs e)
            {
                // New control added to new result viewer window.
                WindowCreated(e.WebTestResultViewer);
            }

    private void WindowCreated(WebTestResultViewer viewer)        {            // Instantiate an instance of the resultControl referenced in the WebPerfTestResultsViewerControl project.
                resultControl resultControl = new resultControl();            // Add to the dictionary of open playback windows.            System.Diagnostics.Debug.Assert(!m_controls.ContainsKey(viewer.TestResultId));            List<UserControl> userControls = new List<UserControl>();            userControls.Add(resultControl);            // Add Guid to the m_control List to manage Result viewers and controls.            m_controls.Add(viewer.TestResultId, userControls);            // Add tabs to the playback control.            resultControl.Dock = DockStyle.Fill;            viewer.AddResultPage(new Guid(), "Sample", resultControl);        }
    ```

17. Dodaj następujący kod do klasy Połącz, aby utworzyć metodę WebTestResultViewer_SelectedChanged dla programu obsługi zdarzeń loadtestpackageext.webtestresultviewerext.selectionchanged, które zostały dodane w metodzie OnConnection:

    ```csharp
    void WebTestResultViewer_SelectedChanged(object sender, WebTestResultViewerExt.SelectionChangedEventArgs e)
    {
        foreach (UserControl userControl in m_controls[e.TestResultId])            {                // Update the userControl in each result viewer.                resultControl resultControl = userControl as resultControl;                if (resultControl != null)                    // Call the resultControl's Update method (This will be added in the next procedure).                    resultControl.Update(e.WebTestRequestResult);            }
    }
    ```

18. Dodaj następujący kod do klasy Połącz, aby utworzyć metodę WebTesResultViewer_WindowClosed dla programu obsługi zdarzeń loadtestpackageext.webtestresultviewerext.WindowClosed, które zostały dodane w metodzie OnConnection:

    ```csharp
    void WebTesResultViewer_WindowClosed(object sender, WebTestResultViewerExt.WindowClosedEventArgs e)
    {
        if (m_controls.ContainsKey(e.WebTestResultViewer.TestResultId))
        {
            m_controls.Remove(e.WebTestResultViewer.TestResultId);
        }
    }
    ```

     Teraz, gdy kod zostało wykonany na potrzeby dodatku programu Visual Studio, należy dodać metodę Update do obiektu resultControl w projekcie WebPerfTestResultsViewerControl.

## <a name="add-code-to-the-webperftestresultsviewercontrol"></a>Dodaj kod do dodatku WebPerfTestResultsViewerControl

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu WebPerfTestResultsViewerControl i wybierz **właściwości**.

2. Wybierz kartę **aplikacja** , a następnie wybierz listę rozwijaną **platforma docelowa** i wybierz pozycję **.NET Framework 4** (lub nowszy). Zamknij okno **Właściwości** .

   Jest to wymagane w celu obsługi odwołań biblioteki DLL, które są potrzebne do rozszerzania **podglądu wyników testu wydajności sieci Web**.

3. W **Eksploratora rozwiązań**, w projekcie WebPerfTestResultsViewerControl kliknij prawym przyciskiem myszy **odwołania** a następnie wybierz węzeł **Dodaj odwołanie**.

4. W **Dodaj odwołanie** okno dialogowe, kliknij przycisk **.NET** kartę.

5. Przewiń w dół i wybierz **Microsoft.VisualStudio.QualityTools.WebTestFramework**.

6. Wybierz **OK**.

7. W *UserControl1.cs* Dodaj następujące instrukcje Using:

    ```csharp
    using Microsoft.VisualStudio.TestTools.WebTesting;
    using Microsoft.VisualStudio.TestTools.WebTesting.Rules;
    ```

8. Dodaj metodę aktualizacji, która jest nazywana i przekazywana jako WebTestRequestResult z metody WebPerfTestResultsViewerAddin WebTestResultViewer_SelectedChanged w *Connect.cs* pliku. Metoda Aktualizuj zapełnia DataGridView różne właściwości przekazany w WebTestRequestResult.

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

- Na **kompilacji** menu, wybierz opcję **Kompiluj rozwiązanie**.

## <a name="register-the-webperftestresultsvieweraddin-add-in"></a>Zarejestruj dodatek WebPerfTestResultsViewerAddin

1. Na **narzędzia** menu, wybierz opcję **Add-in Manager**.

2. **Add-in Manager** zostanie wyświetlone okno dialogowe.

3. Zaznacz pole wyboru dla dodatku WebPerfTestResultsViewerAddin w **dostępne dodatki** kolumny i wyczyść pola wyboru **uruchamiania** i **wiersza polecenia**kolumn.

4. Wybierz **OK**.

## <a name="run-the-web-performance-test-using-the-web-test-results-viewer"></a>Uruchamianie testu wydajności sieci Web za pomocą przeglądarki Wyniki testów sieci Web

1. Uruchamianie testu wydajności sieci web, a następnie zostanie wyświetlony dodatku WebPerfTestResultsViewerAddin w nowej karcie zatytułowaną przykład, wyświetlaną w **Podgląd wyników testu wydajności sieci Web**.

2. Wybierz kartę Aby wyświetlić właściwości przedstawione w formancie DataGridView.

## <a name="net-security"></a>Zabezpieczenia platformy .NET

Aby zwiększyć bezpieczeństwo poprzez uniemożliwienie automatycznego uaktywniania szkodliwych dodatków, program Visual Studio udostępnia ustawienia na **opcje narzędzi** stronę o nazwie **Dodaj dodatków/makr zabezpieczeń**.

Ponadto ta strona opcji pozwala określić foldery, w których program Visual Studio szuka *. Dodatek* pliki rejestracji. Zwiększa to bezpieczeństwo pozwalając ograniczyć lokalizacje gdzie *. Dodatek* mogą być odczytywane pliki rejestracji. Pozwala to zapobiec złośliwego *. Dodatek* pliki z nieumyślnemu używaniu.

**Ustawienia zabezpieczeń dodatku**

Ustawienia na stronie opcje dla dodatku zabezpieczeń są następujące:

- **Zezwalaj składnikom dodatku na ładowanie.** Domyślnie wybrana. Po wybraniu, dodatki mogą ładować w programie Visual Studio. Gdy nie dokonano zaznaczenia, dodatki mają zakaz załadunku w programie Visual Studio.

- **Zezwalaj na składniki dodatku na ładowanie z adresu URL.** Nie jest zaznaczone domyślnie. Po wybraniu, dodatki mogą być ładowane z zewnętrznych witryn sieci Web. Gdy nie dokonano zaznaczenia, zdalne dodatki mają zakaz załadunku w programie Visual Studio. Jeśli z jakiegoś powodu nie można załadować dodatku, następnie go nie można załadować z sieci Web. To ustawienie kontroluje tylko ładowanie dodatku DLL. *. Dodatek* pliki rejestracji muszą się znajdować w systemie lokalnym.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.UserControl>
- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules>
- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.DataGrid>
- [Tworzenie niestandardowych kodów i wtyczek dla testów obciążenia](../test/create-custom-code-and-plug-ins-for-load-tests.md)
