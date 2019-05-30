---
title: Dodawanie wyszukiwania do okna narzędzi | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ab733e42e883816e5f9a6e8fb513bfd6267a9b5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66309914"
---
# <a name="add-search-to-a-tool-window"></a>Dodawanie wyszukiwania do okna narzędzi
Podczas tworzenia lub aktualizowania okna narzędzi w rozszerzeniu, możesz dodać te same funkcje wyszukiwania, który pojawia się gdzie indziej w programie Visual Studio. Ta funkcja obejmuje następujące funkcje:

- Pole wyszukiwania znajduje się zawsze w obszarze niestandardowego paska narzędzi.

- Wskaźnik postępu, który jest nałożony na samo pole wyszukiwania.

- Możliwości, aby wyświetlić wyniki, natychmiast po wprowadzeniu każdego znaku (Wyszukaj), lub tylko wtedy, gdy wybierzesz **Enter** klucza (Wyszukaj na żądanie).

- Lista, która wyświetla warunki, dla których wyszukaniu ostatnio.

- Możliwość filtrowania wyszukiwania według określonych pól lub aspektów celów wyszukiwania.

Dzięki temu przewodnikowi dowiesz się, jak wykonywać następujące zadania:

1. Tworzenie projektu pakietu VSPackage.

2. Utwórz okna narzędzi, który zawiera kontrolkę użytkownika platformy za pomocą TextBox tylko do odczytu.

3. Dodaj pole wyszukiwania do okna narzędzi.

4. Dodaj implementację wyszukiwania.

5. Włącz szybkie wyszukiwanie i wyświetlanie paska postępu.

6. Dodaj **Uwzględnij wielkość liter** opcji.

7. Dodaj **wyszukiwanie tylko wiersze nawet** filtru.

## <a name="to-create-a-vsix-project"></a>Aby utworzyć projekt VSIX

1. Utwórz projekt VSIX, o nazwie `TestToolWindowSearch` w oknie narzędzi o nazwie **TestSearch**. Jeśli potrzebujesz pomocy w ten sposób, zobacz [Tworzenie rozszerzenia za pomocą okna narzędzia](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="to-create-a-tool-window"></a>Utworzenie okna narzędzia

1. W `TestToolWindowSearch` otwarty projekt *TestSearchControl.xaml* pliku.

2. Zastąp istniejące `<StackPanel>` blok z następujący blok, który dodaje tylko do odczytu <xref:System.Windows.Controls.TextBox> do <xref:System.Windows.Controls.UserControl> w oknie narzędzia.

    ```xaml
    <StackPanel Orientation="Vertical">
        <TextBox Name="resultsTextBox" Height="800.0"
            Width="800.0"
            IsReadOnly="True">
        </TextBox>
    </StackPanel>
    ```

3. W *TestSearchControl.xaml.cs* plików, dodaj następującą instrukcję using:

    ```csharp
    using System.Text;
    ```

4. Usuń `button1_Click()` metody.

     W **TestSearchControl** klasy, Dodaj następujący kod.

     Ten kod dodaje publiczny <xref:System.Windows.Controls.TextBox> właściwość o nazwie **SearchResultsTextBox** i właściwość publicznego ciągu o nazwie **SearchContent**. W Konstruktorze SearchResultsTextBox jest ustawiony do pola tekstowego, a SearchContent jest zainicjowany na zestaw ciągów rozdzielonych znakami nowego wiersza. Zawartość pola tekstowego, również jest ustawiana na zestaw ciągów.

     [!code-csharp[ToolWindowSearch#1](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs)]
     [!code-vb[ToolWindowSearch#1](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]

5. Skompiluj projekt, a następnie rozpocząć debugowanie. Pojawi się doświadczalnym wystąpieniu programu Visual Studio.

6. Na pasku menu wybierz **widoku** > **Windows inne** > **TestSearch**.

     Zostanie wyświetlone okno narzędzia, ale nie jest jeszcze wyświetlany formantu wyszukiwania.

## <a name="to-add-a-search-box-to-the-tool-window"></a>Aby dodać pole wyszukiwania do okna narzędzi

1. W *TestSearch.cs* Dodaj następujący kod, aby `TestSearch` klasy. Ten kod zastępuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> właściwość tak, że metody dostępu get zwraca `true`.

     Aby włączyć wyszukiwanie, konieczne jest przesłonięcie <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> właściwości. <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> Klasy implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> i udostępnia domyślną implementację, które nie umożliwiają wyszukiwanie.

    ```csharp
    public override bool SearchEnabled
    {
        get { return true; }
    }
    ```

2. Skompiluj projekt, a następnie rozpocząć debugowanie. Zostanie wyświetlone wystąpienie eksperymentalne.

3. W doświadczalnym wystąpieniu programu Visual Studio, otwórz **TestSearch**.

     Kontrolka wyszukiwania pojawi się w górnej części okna narzędzia z **wyszukiwania** znaku wodnego oraz ikonę szkła powiększanie. Jednak wyszukiwania nie działa jeszcze, ponieważ proces wyszukiwania nie została zaimplementowana.

## <a name="to-add-the-search-implementation"></a>Aby dodać implementacji wyszukiwania
 Po włączeniu wyszukiwania na <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>, jak w poprzedniej procedurze okna narzędzia tworzy hosta wyszukiwania. Ten host konfiguruje i zarządza procesami wyszukiwania, które pojawiają się w wątku tła. Ponieważ <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> klasa zarządza tworzenia hosta wyszukiwania i ustawienia wyszukiwania, wystarczy utworzyć zadanie wyszukiwania i stanowią metodę wyszukiwania. Proces wyszukiwania występuje w wątku w tle i wywołania formant okna narzędzia występuje w wątku interfejsu użytkownika. W związku z tym, należy użyć [ThreadHelper.Invoke*](https://msdn.microsoft.com/data/ee197798(v=vs.85)) metodę, aby zarządzać wszelkie wywołania, wprowadzone w radzenia sobie z kontrolką.

1. W *TestSearch.cs* plików, Dodaj następujący kod `using` instrukcji:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Runtime.InteropServices;
    using System.Text;
    using System.Windows.Controls;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.PlatformUI;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

2. W `TestSearch` klasy, Dodaj następujący kod, który wykonuje następujące czynności:

    - Zastępuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> metodę w celu utworzenia zadania wyszukiwania.

    - Zastępuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> metody w celu przywrócenia stanu pola tekstowego. Ta metoda jest wywoływana, gdy użytkownik anuluje zadania wyszukiwania i po użytkownik ustawia lub unsets opcji lub filtrów. Zarówno <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> są wywoływane w wątku interfejsu użytkownika. W związku z tym, nie trzeba w tym polu tekstowym za dostęp [ThreadHelper.Invoke*](https://msdn.microsoft.com/data/ee197798(v=vs.85)) metody.

    - Tworzy klasę o nazwie `TestSearchTask` tej, która dziedziczy <xref:Microsoft.VisualStudio.Shell.VsSearchTask>, która udostępnia domyślną implementację elementu <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>.

         W `TestSearchTask`, Konstruktor określa pola prywatnego, który odwołuje się do okna narzędzi. Aby zapewnić metoda wyszukiwania, możesz zastąpić <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> i <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A> metody. <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> Metoda polega na to, gdzie wdrożyć proces wyszukiwania. Ten proces obejmuje wyszukiwania, wyświetlania wyników wyszukiwania w polu tekstowym i wywoływania implementacji klasy podstawowej przez tę metodę, aby zgłosić, że wyszukiwania została zakończona.

    ```csharp
    public override IVsSearchTask CreateSearch(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback)
    {
        if (pSearchQuery == null || pSearchCallback == null)
            return null;
         return new TestSearchTask(dwCookie, pSearchQuery, pSearchCallback, this);
    }

    public override void ClearSearch()
    {
        TestSearchControl control = (TestSearchControl)this.Content;
        control.SearchResultsTextBox.Text = control.SearchContent;
    }

    internal class TestSearchTask : VsSearchTask
    {
        private TestSearch m_toolWindow;

        public TestSearchTask(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback, TestSearch toolwindow)
            : base(dwCookie, pSearchQuery, pSearchCallback)
        {
            m_toolWindow = toolwindow;
        }

        protected override void OnStartSearch()
        {
            // Use the original content of the text box as the target of the search.
            var separator = new string[] { Environment.NewLine };
            TestSearchControl control = (TestSearchControl)m_toolWindow.Content;
            string[] contentArr = control.SearchContent.Split(separator, StringSplitOptions.None);

            // Get the search option.
            bool matchCase = false;
            // matchCase = m_toolWindow.MatchCaseOption.Value;

                // Set variables that are used in the finally block.
                StringBuilder sb = new StringBuilder("");
                uint resultCount = 0;
                this.ErrorCode = VSConstants.S_OK;

                try
                {
                    string searchString = this.SearchQuery.SearchString;

                    // Determine the results.
                    uint progress = 0;
                    foreach (string line in contentArr)
                    {
                        if (matchCase == true)
                        {
                            if (line.Contains(searchString))
                            {
                                sb.AppendLine(line);
                                resultCount++;
                            }
                        }
                        else
                            {
                                if (line.ToLower().Contains(searchString.ToLower()))
                                {
                                    sb.AppendLine(line);
                                    resultCount++;
                                }
                            }

                            // SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));

                            // Uncomment the following line to demonstrate the progress bar.
                            // System.Threading.Thread.Sleep(100);
                        }
                    }
                    catch (Exception e)
                    {
                        this.ErrorCode = VSConstants.E_FAIL;
                    }
                    finally
                    {
                        ThreadHelper.Generic.Invoke(() =>
                        { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });

                        this.SearchResults = resultCount;
                    }

            // Call the implementation of this method in the base class.
            // This sets the task status to complete and reports task completion.
            base.OnStartSearch();
        }

        protected override void OnStopSearch()
        {
            this.SearchResults = 0;
        }
    }
    ```

3. Testowania implementacji wyszukiwania, wykonując następujące czynności:

    1. Skompiluj ponownie projekt, a następnie rozpocząć debugowanie.

    2. W doświadczalnym wystąpieniu programu Visual Studio, otwórz ponownie okno narzędzia, wprowadź jakiś tekst wyszukiwania w oknie wyszukiwania, a następnie kliknij przycisk **ENTER**.

         Powinna pojawić się poprawne wyniki.

## <a name="to-customize-the-search-behavior"></a>Aby dostosować zachowanie wyszukiwania
 Zmieniając ustawienia wyszukiwania, możesz wprowadzać szereg zmian w sposób wyświetlania kontrolki wyszukiwania i jak przeprowadza się wyszukiwanie. Na przykład możesz zmienić znaku wodnego (domyślny tekst wyświetlany w polu wyszukiwania), minimalna i maksymalną szerokość kontrolki wyszukiwania i czy jest wyświetlany pasek postępu. Można również zmienić punkt, w której wyniki wyszukiwania start (na żądanie lub szybkiego wyszukiwania) i czy ma być wyświetlana lista warunków, dla których niedawno Przeszukano. Można znaleźć pełną listę ustawień w <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource> klasy.

1. W * TestSearch.cs* Dodaj następujący kod, aby `TestSearch` klasy. Ten kod umożliwia szybkie wyszukiwanie, zamiast wyszukiwania na żądanie (co oznacza, że użytkownik nie ma kliknij **ENTER**). Ten kod zastępuje `ProvideSearchSettings` method in Class metoda `TestSearch` klasy, które są niezbędne do zmiany ustawień domyślnych.

    ```csharp
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)
    {
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchStartTypeProperty.Name,
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}
    ```

2. Testowanie nowe ustawienie, ponownie skompilować rozwiązanie i ponownego uruchamiania debugera.

     Wyniki wyszukiwania wyświetlany za każdym razem w polu wyszukiwania, wpisz znak.

3. W `ProvideSearchSettings` metody, Dodaj następujący wiersz, który umożliwia wyświetlanie paska postępu.

    ```csharp
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)
    {
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchStartTypeProperty.Name,
             (uint)VSSEARCHSTARTTYPE.SST_INSTANT);
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchProgressTypeProperty.Name,
             (uint)VSSEARCHPROGRESSTYPE.SPT_DETERMINATE);
    }
    ```

     Pasek postępu są wyświetlane należy podać postęp. Aby raportować postęp, Usuń komentarz następujący kod w `OnStartSearch` metody `TestSearchTask` klasy:

    ```csharp
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));
    ```

4. Do wydłużenia wystarczająco postęp przetwarzania paska jest widoczny, Usuń komentarz następujący wiersz w `OnStartSearch` metody `TestSearchTask` klasy:

    ```csharp
    System.Threading.Thread.Sleep(100);
    ```

5. Przetestuj nowe ustawienia, ponownie skompilować rozwiązanie i uruchamianie na potrzeby debugowania.

     Pasek postępu postać w oknie wyszukiwania (niebieska linia poniżej w polu tekstowym wyszukiwania) zawsze wykonywania wyszukiwania.

## <a name="to-enable-users-to-refine-their-searches"></a>Aby umożliwić użytkownikom udoskonalić swoje wyszukiwanie
 Możesz zezwalać użytkownikom zawęzić ich wyszukiwania za pomocą opcji, takich jak **Uwzględnij wielkość liter** lub **Uwzględnij całe wyrazy**. Opcje mogą być wartość logiczna, której są wyświetlane jako pola wyboru lub polecenia, które są wyświetlane jako przyciski. W tym przewodniku utworzysz logiczna opcji.

1. W *TestSearch.cs* Dodaj następujący kod, aby `TestSearch` klasy. Ten kod zastępuje `SearchOptionsEnum` metody, która umożliwia implementacji wyszukiwania wykryć, czy danej opcji jest włączone czy wyłączone. Kod w `SearchOptionsEnum` dodaje możliwość Uwzględnij wielkość liter do <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions> modułu wyliczającego. Możliwość Uwzględnij wielkość liter jest również udostępniana jako `MatchCaseOption` właściwości.

    ```csharp
    private IVsEnumWindowSearchOptions m_optionsEnum;
    public override IVsEnumWindowSearchOptions SearchOptionsEnum
    {
        get
        {
            if (m_optionsEnum == null)
            {
                List<IVsWindowSearchOption> list = new List<IVsWindowSearchOption>();

                list.Add(this.MatchCaseOption);

                m_optionsEnum = new WindowSearchOptionEnumerator(list) as IVsEnumWindowSearchOptions;
            }
            return m_optionsEnum;
        }
    }

    private WindowSearchBooleanOption m_matchCaseOption;
    public WindowSearchBooleanOption MatchCaseOption
    {
        get
        {
            if (m_matchCaseOption == null)
            {
                m_matchCaseOption = new WindowSearchBooleanOption("Match case", "Match case", false);
            }
            return m_matchCaseOption;
        }
    }
    ```

2. W `TestSearchTask` klasy, Usuń komentarz następujące linię `OnStartSearch` metody:

    ```csharp
    matchCase = m_toolWindow.MatchCaseOption.Value;
    ```

3. Przetestuj opcji:

    1. Skompiluj projekt, a następnie rozpocząć debugowanie. Zostanie wyświetlone wystąpienie eksperymentalne.

    2. W oknie Narzędzia wybierz strzałkę w dół po prawej stronie pola tekstowego.

         **Uwzględnij wielkość liter** pojawi się pole wyboru.

    3. Wybierz **Uwzględnij wielkość liter** pole wyboru, a następnie wykonać niektóre wyszukiwania.

## <a name="to-add-a-search-filter"></a>Aby dodać filtr wyszukiwania
 Można dodać filtry wyszukiwania, które umożliwiają użytkownikom uściślenia zestawu elementów docelowych wyszukiwania. Na przykład można filtrować pliki w Eksploratorze plików, według daty, od których one zostały ostatnio zmodyfikowane i ich rozszerzenia nazw plików. W tym przewodniku dodasz filtr tylko nawet wiersze. Gdy użytkownik wybierze ten filtr, hosta wyszukiwania dodaje ciągów, które można określić do zapytania wyszukiwania. Można zidentyfikować te ciągi wewnątrz metodę wyszukiwania i filtrowania elementów docelowych wyszukiwania odpowiednio.

1. W *TestSearch.cs* Dodaj następujący kod, aby `TestSearch` klasy. Kod implementuje `SearchFiltersEnum` , dodając <xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter> określający do odfiltrowania wyników wyszukiwania, tak aby były wyświetlane tylko nawet wiersze.

    ```csharp
    public override IVsEnumWindowSearchFilters SearchFiltersEnum
    {
        get
        {
            List<IVsWindowSearchFilter> list = new List<IVsWindowSearchFilter>();
            list.Add(new WindowSearchSimpleFilter("Search even lines only", "Search even lines only", "lines", "even"));
            return new WindowSearchFilterEnumerator(list) as IVsEnumWindowSearchFilters;
        }
    }

    ```

     Teraz kontrolka wyszukiwania zawiera filtr wyszukiwania `Search even lines only`. Kiedy użytkownik naciśnie filtr ciąg `lines:"even"` pojawia się w polu wyszukiwania. Kryteria wyszukiwania może znajdować się w tym samym czasie jako filtr. Wyszukiwanie ciągów może pojawić się przed filtru, po filtr i / lub.

2. W *TestSearch.cs* Dodaj następujące metody umożliwiające `TestSearchTask` klasy, która znajduje się w `TestSearch` klasy. Metody te obsługują `OnStartSearch` metody, która zmodyfikujesz w następnym kroku.

    ```csharp
    private string RemoveFromString(string origString, string stringToRemove)
    {
        int index = origString.IndexOf(stringToRemove);
        if (index == -1)
            return origString;
        else 
             return (origString.Substring(0, index) + origString.Substring(index + stringToRemove.Length)).Trim();
    }

    private string[] GetEvenItems(string[] contentArr)
    {
        int length = contentArr.Length / 2;
        string[] evenContentArr = new string[length];

        int indexB = 0;
        for (int index = 1; index < contentArr.Length; index += 2)
        {
            evenContentArr[indexB] = contentArr[index];
            indexB++;
        }

        return evenContentArr;
    }
    ```

3. W `TestSearchTask` klasy, zaktualizuj `OnStartSearch` metoda następującym kodem. Ta zmiana aktualizuje kod w celu obsługi filtru.

    ```csharp
    protected override void OnStartSearch()
    {
        // Use the original content of the text box as the target of the search. 
        var separator = new string[] { Environment.NewLine };
        string[] contentArr = ((TestSearchControl)m_toolWindow.Content).SearchContent.Split(separator, StringSplitOptions.None);

        // Get the search option. 
        bool matchCase = false;
        matchCase = m_toolWindow.MatchCaseOption.Value;

        // Set variables that are used in the finally block.
        StringBuilder sb = new StringBuilder("");
        uint resultCount = 0;
        this.ErrorCode = VSConstants.S_OK;

        try
        {
            string searchString = this.SearchQuery.SearchString;

            // If the search string contains the filter string, filter the content array. 
            string filterString = "lines:\"even\"";

            if (this.SearchQuery.SearchString.Contains(filterString))
            {
                // Retain only the even items in the array.
                contentArr = GetEvenItems(contentArr);

                // Remove 'lines:"even"' from the search string.
                searchString = RemoveFromString(searchString, filterString);
            }

            // Determine the results. 
            uint progress = 0;
            foreach (string line in contentArr)
            {
                if (matchCase == true)
                {
                    if (line.Contains(searchString))
                    {
                        sb.AppendLine(line);
                        resultCount++;
                    }
                }
                else
                {
                    if (line.ToLower().Contains(searchString.ToLower()))
                    {
                        sb.AppendLine(line);
                        resultCount++;
                    }
                }

                SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));

                // Uncomment the following line to demonstrate the progress bar. 
                // System.Threading.Thread.Sleep(100);
            }
        }
        catch (Exception e)
        {
            this.ErrorCode = VSConstants.E_FAIL;
        }
        finally
        {
            ThreadHelper.Generic.Invoke(() =>
            { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });

            this.SearchResults = resultCount;
        }

        // Call the implementation of this method in the base class. 
        // This sets the task status to complete and reports task completion. 
        base.OnStartSearch();
    }
    ```

4. Przetestuj swój kod.

5. Skompiluj projekt, a następnie rozpocząć debugowanie. W doświadczalnym wystąpieniu programu Visual Studio Otwórz okno narzędzia, a następnie kliknij strzałkę w dół na kontrolce wyszukiwania.

     **Uwzględnij wielkość liter** pole wyboru i **wyszukiwanie tylko wiersze nawet** filtru są wyświetlane.

6. Wybierz odpowiedni filtr.

     Zawiera pole wyszukiwania **wierszy: "nawet"** , i są wyświetlane następujące wyniki:

     dobre 2

     Dobre 4

     6 goodbye

7. Usuń `lines:"even"` w polu wyszukiwania, wybierz **Uwzględnij wielkość liter** pole wyboru, a następnie wprowadź `g` w polu wyszukiwania.

     Wyświetlane są następujące wyniki:

     1 z rzeczywistym użyciem

     dobre 2

     5 goodbye

8. Wybierz X po prawej stronie pola wyszukiwania.

     Wyszukiwanie jest wyczyszczone, a oryginalna zawartość jest wyświetlana. Jednak **Uwzględnij wielkość liter** nadal zaznaczone jest pole wyboru.