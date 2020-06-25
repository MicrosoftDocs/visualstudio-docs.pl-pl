---
title: Tworzenie dodatku dla usługi Web Performance Wyniki testów Viewer
ms.date: 10/20/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, Visual Studio Add-in
- Visual Studio Add-in, Web performance tests
ms.assetid: 1118c604-4b1b-4b21-a04e-45995b676fa8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 736c43a83a956c02b760b4909a427a82c6fa9e4c
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85287834"
---
# <a name="how-to-create-an-add-in-for-the-web-performance-test-results-viewer"></a>Instrukcje: Tworzenie dodatku dla usługi Web Performance Wyniki testów Viewer

Interfejs użytkownika dla **przeglądarki wyniki testów wydajności sieci Web** można rozszerzyć przy użyciu następujących przestrzeni nazw:

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>

- <xref:Microsoft.VisualStudio.TestTools.WebTesting>

Ponadto należy dodać odwołanie do biblioteki DLL LoadTestPackage, która znajduje się w folderze *% ProgramFiles (x86)% \ Microsoft Visual Studio \\ \<version> \Enterprise\Common7\IDE\PrivateAssemblies* .

Aby zwiększyć interfejs użytkownika w **przeglądarce wyniki testów wydajności sieci Web**, należy utworzyć dodatek programu Visual Studio i kontrolkę użytkownika. W poniższych procedurach opisano sposób tworzenia dodatku, kontrolki użytkownika oraz sposób implementowania klas niezbędnych do rozbudowania interfejsu użytkownika w **przeglądarce wyniki testów wydajności sieci Web**.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="create-or-open-a-solution-that-contains-an-aspnet-web-application-and-a-web-performance-and-load-test-project"></a>Utwórz lub Otwórz rozwiązanie, które zawiera aplikację sieci Web ASP.NET oraz projekt testu wydajności i obciążenia sieci Web

### <a name="to-prepare-for-extending-the-web-performance-test-results-viewer"></a>Aby przygotować się do rozszerzenia podglądu wydajności sieci Web Wyniki testów

Utwórz lub Otwórz rozwiązanie nieprodukcyjne, z którym można eksperymentować, które zawiera aplikację sieci Web ASP.NET oraz projekt testów wydajności sieci Web i obciążenia z co najmniej jednym testem wydajności sieci Web dla aplikacji sieci Web ASP.NET.

> [!NOTE]
> Można utworzyć aplikację sieci Web ASP.NET oraz projekt testów wydajności sieci Web i obciążenia, który zawiera testy wydajności sieci Web, wykonując procedury opisane w temacie [jak utworzyć test usługi sieci Web](../test/how-to-create-a-web-service-test.md) i [generować i uruchamiać kodowane testy wydajności sieci Web](../test/generate-and-run-a-coded-web-performance-test.md).

## <a name="create-a-visual-studio-add-in"></a>Tworzenie dodatku programu Visual Studio

Dodatek jest skompilowaną biblioteką DLL, która działa w zintegrowanym środowisku programistycznym (IDE) programu Visual Studio. Kompilacja pomaga chronić własność intelektualną i zwiększa wydajność. Mimo że dodatki można tworzyć ręcznie, łatwiej jest użyć **kreatora dodatków**. Ten Kreator tworzy funkcjonalny, ale podstawowy dodatek, który można uruchomić natychmiast po jego utworzeniu. Gdy **Kreator dodatku** wygeneruje podstawowy program, można dodać do niego kod i dostosować go.

**Kreator dodatku** pozwala podać nazwę wyświetlaną i opis dla dodatku. Oba będą widoczne w **Menedżerze dodatków**. Opcjonalnie możesz utworzyć przez kreatora kod, który dodaje do menu **Narzędzia** polecenie, aby otworzyć dodatek. Możesz również wybrać opcję wyświetlania niestandardowego okna dialogowego **informacje** dla dodatku. Po zakończeniu pracy Kreatora istnieje nowy projekt, który ma tylko jedną klasę, która implementuje dodatek. Ta klasa ma nazwę Connect.

Na końcu tego artykułu zostanie użyty **Menedżer dodatków** .

### <a name="to-create-an-add-in-by-using-the-add-in-wizard"></a>Aby utworzyć dodatek przy użyciu kreatora dodatków

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy rozwiązanie, wybierz polecenie **Dodaj**, a następnie wybierz pozycję **Nowy projekt**.

2. Utwórz nowy projekt **dodatku programu Visual Studio** .

    Zostanie uruchomiony **Kreator dodatku** programu Visual Studio.

3. Wybierz pozycję **Next** (Dalej).

4. Na stronie **Wybierz język programowania** wybierz język programowania, którego chcesz użyć do napisania dodatku.

   > [!NOTE]
   > Ten temat używa języka Visual C# dla przykładowego kodu.

5. Na stronie **Wybierz hosta aplikacji** wybierz pozycję **Visual Studio** i wyczyść **makra programu Visual Studio**.

6. Wybierz pozycję **Next** (Dalej).

7. Wpisz nazwę i Opis dodatku na stronie **Wprowadź nazwę i opis** .

     Po utworzeniu dodatku jego nazwa i opis są wyświetlane na liście **dostępne dodatki** w **Menedżerze dodatków**. Dodaj wystarczającą ilość szczegółów do opisu dodatku, aby użytkownicy mogli dowiedzieć się, co to jest dodatek, jak działa i tak dalej.

8. Wybierz pozycję **Next** (Dalej).

9. Na stronie **Wybierz Opcje dodatku** wybierz opcję **Chcę załadować dodatek, gdy aplikacja hosta zostanie uruchomiona**.

10. Wyczyść pozostałe pola wyboru.

11. Na stronie **Wybieranie informacji o pomocy dotyczącej** programu można określić, czy informacje o dodatku mają być wyświetlane w oknie dialogowym **informacje** . Jeśli chcesz, aby informacje były wyświetlane, wybierz opcję **tak, chcę dodać informacje o polu "informacje"** .

     Informacje, które można dodać do okna dialogowego **Informacje o** programie Visual Studio zawierają numer wersji, szczegóły pomocy technicznej, dane licencyjne i tak dalej.

12. Wybierz pozycję **Next** (Dalej).

13. Wybrane opcje są wyświetlane na stronie **Podsumowanie** , aby przejrzeć. Jeśli masz pewność, wybierz pozycję **Zakończ** , aby utworzyć dodatek. Jeśli chcesz zmienić coś, wybierz przycisk **Wstecz** .

     Zostanie utworzone nowe rozwiązanie i projekt, a plik *Connect.cs* dla nowego dodatku zostanie wyświetlony w **edytorze kodu**.

     Po następującej procedurze zostanie dodany kod do pliku *Connect.cs* , który tworzy formant użytkownika, do którego odwołuje się ten projekt WebPerfTestResultsViewerAddin.

    Po utworzeniu dodatku należy zarejestrować go w programie Visual Studio, zanim będzie można aktywować go w **Menedżerze dodatków**. Można to zrobić za pomocą pliku XML, który ma rozszerzenie nazwy pliku *. addin* .

    Plik *. addin* zawiera opis informacji wymaganych przez program Visual Studio do wyświetlania dodatku w **Menedżerze dodatków**. Po uruchomieniu programu Visual Studio szuka on w lokalizacji pliku *. addin* dla dowolnych dostępnych plików *. addin* . W przypadku znalezienia któregoś z nich odczytuje plik XML i zapewnia **menedżerowi dodatków** informacje wymagane do uruchomienia dodatku, gdy zostanie kliknięty.

    Plik *. addin* jest tworzony automatycznie podczas tworzenia dodatku za pomocą **kreatora dodatków**.

### <a name="add-in-file-locations"></a>Lokalizacje plików dodatków

Dwie kopie plików *. addin* są tworzone automatycznie przez **kreatora dodatków**w następujący sposób:

|**. Lokalizacja pliku dodatku**|**Opis**|
|-|----------------------------|-|
|Folder główny projektu|Używane do wdrażania projektu dodatku. Zawarte w projekcie w celu ułatwienia edycji i ma ścieżkę lokalną dla wdrożenia w stylu XCopy.|
|Folder dodatków|Używany do uruchamiania dodatku w środowisku debugowania. Powinien zawsze wskazywać ścieżkę wyjściową bieżącej konfiguracji kompilacji.|

## <a name="create-a-windows-form-control-library-project"></a>Tworzenie projektu biblioteki formantów formularzy systemu Windows

Dodatek Visual Studio utworzony w poprzedniej procedurze odwołuje się do projektu biblioteki formantów Windows Forms, aby utworzyć wystąpienie <xref:System.Windows.Forms.UserControl> klasy.

### <a name="to-create-a-control-to-be-used-in-the-web-test-results-viewer"></a>Aby utworzyć kontrolkę, która ma być używana w przeglądarce Wyniki testów sieci Web

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy rozwiązanie, wybierz polecenie **Dodaj**, a następnie wybierz pozycję **Nowy projekt**.

2. Utwórz nowy projekt **biblioteki formantów Windows Forms** .

3. Z **przybornika**przeciągnij a na <xref:System.Windows.Forms.DataGridView> powierzchnię UserControl1.

4. Kliknij symbol tagu akcji ( ![ symbol tagu inteligentnego ](../test/media/vs_winformsmttagglyph.gif) ) w prawym górnym rogu <xref:System.Windows.Forms.DataGridView> i wykonaj następujące kroki:

    1. Wybierz pozycję **Zadokuj w kontenerze nadrzędnym**.

    2. Wyczyść pola wyboru **Włącz Dodawanie**, **Włącz edytowanie**, **Włącz usuwanie** i **Włącz zmianę kolejności kolumn**.

    3. Wybierz pozycję **Dodaj kolumnę**.

         Zostanie wyświetlone okno dialogowe **Dodaj kolumnę** .

    4. Z listy rozwijanej **Typ** wybierz pozycję **DataGridViewTextBoxColumn**.

    5. Wyczyść tekst "Kolumna1" w **tekście nagłówka**.

    6. Wybierz pozycję **Dodaj**.

    7. Wybierz pozycję **Zamknij**.

5. W oknie **Właściwości** Zmień właściwość **(nazwa)** elementu <xref:System.Windows.Forms.DataGridView> na **resultControlDataGridView**.

6. Kliknij prawym przyciskiem myszy powierzchnię projektu i wybierz polecenie **Wyświetl kod**.

     Plik *UserControl1.cs* jest wyświetlany w **edytorze kodu**.

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

     W następnej procedurze zostanie dodany kod do pliku *Connect.cs* projektu WebPerfTestResultsViewerAddin, który będzie odwoływać się do klasy resultControl.

     Później zostanie dodany dodatkowy kod do pliku *Connect.cs* .

## <a name="add-code-to-the-webperftestresultsvieweraddin"></a>Dodawanie kodu do WebPerfTestResultsViewerAddin

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł **odwołania** w projekcie WebPerfTestResultsViewerAddin i wybierz polecenie **Dodaj odwołanie**.

2. W oknie dialogowym **Dodaj odwołanie** wybierz kartę **.NET** .

3. Przewiń w dół i wybierz pozycję **Microsoft. VisualStudio. QualityTools. WebTestFramework** i **System. Windows. Forms**.

4. Wybierz przycisk **OK**.

5. Ponownie kliknij prawym przyciskiem myszy węzeł **odwołania** i wybierz polecenie **Dodaj odwołanie**.

6. W oknie dialogowym **Dodaj odwołanie** wybierz kartę **przeglądanie** .

7. Wybierz listę rozwijaną dla opcji **Szukaj w** i przejdź do pliku *% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies* i wybierz plik *Microsoft.VisualStudio.QualityTools.LoadTestPackage.dll* .

8. Wybierz przycisk **OK**.

9. Kliknij prawym przyciskiem myszy węzeł projektu WebPerfTestResultsViewerAddin i wybierz polecenie **Dodaj odwołanie**.

10. W oknie dialogowym **Dodaj odwołanie** wybierz kartę **projekty** .

11. W obszarze **Nazwa projektu**wybierz projekt **WebPerfTestResultsViewerControl** , a następnie wybierz **przycisk OK**.

12. Jeśli plik *Connect.cs* nie jest wciąż otwarty, w **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy plik **Connect.cs** w projekcie WebPerfTestResultsViewerAddin i wybierz polecenie **Wyświetl kod**.

13. W pliku *Connect.cs* Dodaj następujące instrukcje using:

    ```csharp
    using System.IO;
    using System.Windows.Forms;
    using System.Collections.Generic;
    using Microsoft.VisualStudio.TestTools.LoadTesting;
    using Microsoft.VisualStudio.TestTools.WebTesting;
    using WebPerfTestResultsViewerControl;
    ```

14. Przewiń w dół do końca pliku *Connect.cs* . Należy dodać listę identyfikatorów GUID dla programu <xref:System.Windows.Forms.UserControl> w przypadku, gdy więcej niż jedno wystąpienie **przeglądarki wyniki testów wydajności sieci Web** jest otwarte. Później dodasz kod, który używa tej listy.

     Druga lista ciągów jest używana w metodzie OnDiscconection.

    ```csharp
    private DTE2 _applicationObject;
    private AddIn _addInInstance;

    private Dictionary<Guid, List<UserControl>> m_controls = new Dictionary<Guid, List<UserControl>>();        private List<string> temporaryFilePaths = new List<string>();
    ```

15. Plik *Connect.cs* tworzy wystąpienie klasy o nazwie Connect z <xref:Extensibility.IDTExtensibility2> klasy i zawiera również kilka metod implementowania dodatku Visual Studio. Jedną z metod jest metoda OnConnection, która otrzymuje powiadomienie o tym, że dodatek jest ładowany. W metodzie OnConnection należy użyć klasy LoadTestPackageExt do utworzenia pakietu rozszerzalności dla **przeglądarki wyniki testów wydajności sieci Web**. Dodaj następujący kod do metody OnConnection:

    ```csharp
    public void OnConnection(object application, ext_ConnectMode connectMode, object addInInst, ref Array custom)
                {
                _applicationObject = (DTE2)application;
                _addInInstance = (AddIn)addInInst;

                // Create a load test packge extensibility class.            LoadTestPackageExt loadTestPackageExt = _applicationObject.GetObject("Microsoft.VisualStudio.TestTools.LoadTesting.LoadTestPackageExt") as LoadTestPackageExt;            // Process open windows.            foreach (WebTestResultViewer webTestResultViewer in loadTestPackageExt.WebTestResultViewerExt.ResultWindows)            {                WindowCreated(webTestResultViewer);            }            // Create event handlers.            loadTestPackageExt.WebTestResultViewerExt.WindowCreated += new EventHandler<WebTestResultViewerExt.WindowCreatedEventArgs>(WebTestResultViewerExt_WindowCreated);            loadTestPackageExt.WebTestResultViewerExt.WindowClosed += new EventHandler<WebTestResultViewerExt.WindowClosedEventArgs>(WebTesResultViewer_WindowClosed);            loadTestPackageExt.WebTestResultViewerExt.SelectionChanged += new EventHandler<WebTestResultViewerExt.SelectionChangedEventArgs>(WebTestResultViewer_SelectedChanged);
            }
    ```

16. Dodaj następujący kod do klasy Connect, aby utworzyć metodę WebTestResultViewerExt_WindowCreated dla programu obsługi zdarzeń loadTestPackageExt. WebTestResultViewerExt. WindowCreated dodanej w metodzie OnConnection i dla metody WindowCreated, która wywołuje metodę WebTestResultViewerExt_WindowCreated.

    ```csharp
            void WebTestResultViewerExt_WindowCreated(object sender, WebTestResultViewerExt.WindowCreatedEventArgs e)
            {
                // New control added to new result viewer window.
                WindowCreated(e.WebTestResultViewer);
            }

    private void WindowCreated(WebTestResultViewer viewer)        {            // Instantiate an instance of the resultControl referenced in the WebPerfTestResultsViewerControl project.
                resultControl resultControl = new resultControl();            // Add to the dictionary of open playback windows.            System.Diagnostics.Debug.Assert(!m_controls.ContainsKey(viewer.TestResultId));            List<UserControl> userControls = new List<UserControl>();            userControls.Add(resultControl);            // Add Guid to the m_control List to manage Result viewers and controls.            m_controls.Add(viewer.TestResultId, userControls);            // Add tabs to the playback control.            resultControl.Dock = DockStyle.Fill;            viewer.AddResultPage(new Guid(), "Sample", resultControl);        }
    ```

17. Dodaj następujący kod do klasy Connect, aby utworzyć metodę WebTestResultViewer_SelectedChanged dla programu obsługi zdarzeń loadTestPackageExt. WebTestResultViewerExt. SelectionChanged dodanej w metodzie OnConnection:

    ```csharp
    void WebTestResultViewer_SelectedChanged(object sender, WebTestResultViewerExt.SelectionChangedEventArgs e)
    {
        foreach (UserControl userControl in m_controls[e.TestResultId])            {                // Update the userControl in each result viewer.                resultControl resultControl = userControl as resultControl;                if (resultControl != null)                    // Call the resultControl's Update method (This will be added in the next procedure).                    resultControl.Update(e.WebTestRequestResult);            }
    }
    ```

18. Dodaj następujący kod do klasy Connect, aby utworzyć metodę WebTesResultViewer_WindowClosed dla programu obsługi zdarzeń dla loadTestPackageExt. WebTestResultViewerExt. WindowClosed dodanej w metodzie OnConnection:

    ```csharp
    void WebTesResultViewer_WindowClosed(object sender, WebTestResultViewerExt.WindowClosedEventArgs e)
    {
        if (m_controls.ContainsKey(e.WebTestResultViewer.TestResultId))
        {
            m_controls.Remove(e.WebTestResultViewer.TestResultId);
        }
    }
    ```

     Teraz, gdy kod został ukończony dla dodatku Visual Studio, musisz dodać metodę aktualizacji do resultControl w projekcie WebPerfTestResultsViewerControl.

## <a name="add-code-to-the-webperftestresultsviewercontrol"></a>Dodawanie kodu do WebPerfTestResultsViewerControl

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu WebPerfTestResultsViewerControl i wybierz polecenie **Właściwości**.

2. Wybierz kartę **aplikacja** , a następnie wybierz listę rozwijaną **platforma docelowa** i wybierz pozycję **.NET Framework 4** (lub nowszy). Zamknij okno **Właściwości** .

   Jest to wymagane w celu obsługi odwołań do bibliotek DLL, które są potrzebne do rozszerzenia **podglądu wydajności sieci Web wyniki testów**.

3. W **Eksplorator rozwiązań**w projekcie WebPerfTestResultsViewerControl kliknij prawym przyciskiem myszy węzeł **odwołania** i wybierz polecenie **Dodaj odwołanie**.

4. W oknie dialogowym **Dodawanie odwołania** kliknij kartę **.NET** .

5. Przewiń w dół i wybierz pozycję **Microsoft. VisualStudio. QualityTools. WebTestFramework**.

6. Wybierz przycisk **OK**.

7. W pliku *UserControl1.cs* Dodaj następujące instrukcje using:

    ```csharp
    using Microsoft.VisualStudio.TestTools.WebTesting;
    using Microsoft.VisualStudio.TestTools.WebTesting.Rules;
    ```

8. Dodaj metodę Update, która jest wywoływana i przekazała WebTestRequestResult z metody WebPerfTestResultsViewerAddin WebTestResultViewer_SelectedChanged w pliku *Connect.cs* . Metoda Update wypełnia formant DataGridView przy użyciu różnych właściwości przekazaną do niego w WebTestRequestResult.

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

- W menu **kompilacja** wybierz opcję **Kompiluj rozwiązanie**.

## <a name="register-the-webperftestresultsvieweraddin-add-in"></a>Zarejestruj dodatek WebPerfTestResultsViewerAddin

1. W menu **Narzędzia** wybierz pozycję **Menedżer dodatków**.

2. Zostanie wyświetlone okno dialogowe **Menedżer dodatków** .

3. Zaznacz pole wyboru dla dodatku WebPerfTestResultsViewerAddin w kolumnie **dostępne dodatki** i usuń zaznaczenie pól wyboru pod kolumną **Startup** i **wiersz polecenia** .

4. Wybierz przycisk **OK**.

## <a name="run-the-web-performance-test-using-the-web-test-results-viewer"></a>Uruchamianie testu wydajności sieci Web za pomocą przeglądarki Wyniki testów sieci Web

1. Uruchom test wydajności sieci Web i zobaczysz przykład nowej karty WebPerfTestResultsViewerAddin dodatku zatytułowanej, który jest wyświetlany w **przeglądarce wyniki testów wydajności sieci Web**.

2. Wybierz kartę, aby wyświetlić właściwości przedstawione w formancie DataGridView.

## <a name="net-security"></a>Zabezpieczenia platformy .NET

Aby zwiększyć bezpieczeństwo, zapobiegając automatycznej aktywacji szkodliwych dodatków, program Visual Studio udostępnia ustawienia na stronie **Opcje narzędzi** o nazwie **Zabezpieczenia dodatków/makr**.

Ponadto ta strona opcji pozwala określić foldery, w których program Visual Studio wyszukuje *. *Pliki rejestracji dodatków. Zwiększa to bezpieczeństwo przez umożliwienie ograniczenia lokalizacji w miejscu *. *Pliki rejestracji dodatków można odczytać. Pozwala to zapobiec złośliwemu *. Pliki dodatków* z niezamierzonego użycia.

**Ustawienia zabezpieczeń dodatku**

Ustawienia na stronie Opcje zabezpieczeń dodatku są następujące:

- **Zezwalaj składnikom dodatku na ładowanie.** Domyślnie zaznaczony. Po wybraniu Dodatki mogą ładować się w programie Visual Studio. Gdy nie jest zaznaczone, dodatki nie mogą być ładowane w programie Visual Studio.

- **Zezwalaj składnikom dodatku na ładowanie z adresu URL.** Nie wybrano domyślnie. Po wybraniu tej opcję Dodatki mogą być ładowane z zewnętrznych witryn sieci Web. Gdy nie jest zaznaczone, dodatki zdalne nie mogą być ładowane w programie Visual Studio. Jeśli dodatek nie może zostać załadowany z jakiegoś powodu, nie można go załadować z sieci Web. To ustawienie kontroluje tylko ładowanie biblioteki DLL dodatku. *. *Pliki rejestracji dodatków muszą być zawsze zlokalizowane w systemie lokalnym.

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.UserControl>
- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules>
- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.DataGrid>
- [Tworzenie niestandardowych kodów i wtyczek dla testów obciążeniowych](../test/create-custom-code-and-plug-ins-for-load-tests.md)
