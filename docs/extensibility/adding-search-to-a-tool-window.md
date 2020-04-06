---
title: Dodawanie wyszukiwania do okna narzędzia | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f9112a3368ba604c4291f9018e763022e953c4fc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740140"
---
# <a name="add-search-to-a-tool-window"></a>Dodawanie wyszukiwania do okna narzędzia
Podczas tworzenia lub aktualizowania okna narzędzia w rozszerzeniu, można dodać tę samą funkcję wyszukiwania, która pojawia się w innym miejscu w programie Visual Studio. Ta funkcja obejmuje następujące funkcje:

- Pole wyszukiwania, które zawsze znajduje się w niestandardowym obszarze paska narzędzi.

- Wskaźnik postępu, który jest nałożony na samo pole wyszukiwania.

- Możliwość pokazywalania wyników zaraz po wprowadzeniu każdego znaku (wyszukiwanie błyskawiczne) lub dopiero po wybraniu **klawisza Enter** (wyszukiwanie na żądanie).

- Lista zawierająca terminy, dla których ostatnio wyszukiwano.

- Możliwość filtrowania wyszukiwań według określonych pól lub aspektów obiektów docelowych wyszukiwania.

Wykonując ten przewodnik, dowiesz się, jak wykonać następujące zadania:

1. Utwórz projekt VSPackage.

2. Utwórz okno narzędzia zawierające usercontrol z polem tekstowym tylko do odczytu.

3. Dodaj pole wyszukiwania do okna narzędzia.

4. Dodaj implementację wyszukiwania.

5. Włącz natychmiastowe wyszukiwanie i wyświetlanie paska postępu.

6. Dodaj opcję **Dopasuj sprawę.**

7. Dodaj **filtr tylko wiersze parzyste wyszukiwania.**

## <a name="to-create-a-vsix-project"></a>Aby utworzyć projekt VSIX

1. Utwórz projekt VSIX o nazwie `TestToolWindowSearch` z oknem narzędzia o nazwie **TestSearch**. Jeśli potrzebujesz pomocy w tym zakresie, zobacz [Tworzenie rozszerzenia za pomocą okna narzędzia](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="to-create-a-tool-window"></a>Aby utworzyć okno narzędzia

1. W `TestToolWindowSearch` projekcie otwórz plik *TestSearchControl.xaml.*

2. Zastąp istniejący `<StackPanel>` blok następującym blokiem, który dodaje tylko <xref:System.Windows.Controls.TextBox> do odczytu <xref:System.Windows.Controls.UserControl> do okna narzędzia.

    ```xaml
    <StackPanel Orientation="Vertical">
        <TextBox Name="resultsTextBox" Height="800.0"
            Width="800.0"
            IsReadOnly="True">
        </TextBox>
    </StackPanel>
    ```

3. W pliku *TestSearchControl.xaml.cs* dodaj następujące elementy za pomocą dyrektywy:

    ```csharp
    using System.Text;
    ```

4. Usuń `button1_Click()` metodę.

     W **TestSearchControl** klasy, dodaj następujący kod.

     Ten kod dodaje <xref:System.Windows.Controls.TextBox> właściwość publiczną o nazwie **SearchResultsTextBox** i publiczną właściwość ciągu o nazwie **SearchContent**. W konstruktorze SearchResultsTextBox jest ustawiona na pole tekstowe, a SearchContent jest inicjowany do zestawu ciągów rozdzielanych przez nowy. Zawartość pola tekstowego jest również inicjowana do zestawu ciągów.

     [!code-csharp[ToolWindowSearch#1](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs)]
     [!code-vb[ToolWindowSearch#1](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]

5. Skompiluj projekt i rozpocznij debugowanie. Pojawi się eksperymentalne wystąpienie programu Visual Studio.

6. Na pasku menu wybierz pozycję **Wyświetl** > inne**elementy testowe****systemu Windows** > .

     Zostanie wyświetlone okno narzędzia, ale kontrolka wyszukiwania nie jest jeszcze wyświetlana.

## <a name="to-add-a-search-box-to-the-tool-window"></a>Aby dodać pole wyszukiwania do okna narzędzia

1. W pliku *TestSearch.cs* dodaj następujący kod do `TestSearch` klasy. Kod zastępuje właściwość <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> tak, aby get `true`akcesor zwraca .

     Aby włączyć wyszukiwanie, należy zastąpić <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> właściwość. Klasa <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> i udostępnia domyślną implementację, która nie włącza wyszukiwania.

    ```csharp
    public override bool SearchEnabled
    {
        get { return true; }
    }
    ```

2. Skompiluj projekt i rozpocznij debugowanie. Pojawi się eksperymentalne wystąpienie.

3. W eksperymentalnym wystąpieniu programu Visual Studio otwórz **program TestSearch**.

     W górnej części okna narzędzia pojawi się kontrolka wyszukiwania ze znakiem wodnym **wyszukiwania** i ikoną lupy. Jednak wyszukiwanie nie działa jeszcze, ponieważ proces wyszukiwania nie został zaimplementowany.

## <a name="to-add-the-search-implementation"></a>Aby dodać implementację wyszukiwania
 Po włączeniu wyszukiwania <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>na , jak w poprzedniej procedurze, okno narzędzia tworzy hosta wyszukiwania. Ten host konfiguruje i zarządza procesami wyszukiwania, które zawsze występują w wątku w tle. Ponieważ <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> klasa zarządza tworzeniem hosta wyszukiwania i konfigurowaniem wyszukiwania, wystarczy utworzyć zadanie wyszukiwania i podać metodę wyszukiwania. Proces wyszukiwania odbywa się w wątku w tle i wywołania formantu okna narzędzia występują w wątku interfejsu użytkownika. W związku z tym należy użyć [ThreadHelper.Invoke*](https://msdn.microsoft.com/data/ee197798(v=vs.85)) metoda do zarządzania wszelkie wywołania, które można wykonać w kontaktach z formantem.

1. W pliku *TestSearch.cs* dodaj następujące `using` dyrektywy:

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

2. W `TestSearch` klasie dodaj następujący kod, który wykonuje następujące akcje:

    - Zastępuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> metodę tworzenia zadania wyszukiwania.

    - Zastępuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> metodę przywracania stanu pola tekstowego. Ta metoda jest wywoływana, gdy użytkownik anuluje zadanie wyszukiwania i gdy użytkownik ustawia lub unsets opcje lub filtruje. Oba <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> i są wywoływane w wątku interfejsu użytkownika. W związku z tym nie trzeba uzyskać dostępu do pola tekstowego za pomocą [ThreadHelper.Invoke*](https://msdn.microsoft.com/data/ee197798(v=vs.85)) metody.

    - Tworzy klasę o nazwie, `TestSearchTask` która <xref:Microsoft.VisualStudio.Shell.VsSearchTask>dziedziczy z programu <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>, która zapewnia domyślną implementację programu .

         W `TestSearchTask`obszarze konstruktor ustawia pole prywatne, które odwołuje się do okna narzędzia. Aby zapewnić metodę wyszukiwania, należy <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> zastąpić <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A> i metody. Metoda <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> jest, gdzie można zaimplementować proces wyszukiwania. Ten proces obejmuje wykonywanie wyszukiwania, wyświetlanie wyników wyszukiwania w polu tekstowym i wywołanie implementacji klasy podstawowej tej metody w celu zgłoszenia, że wyszukiwanie zostało zakończone.

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

3. Przetestuj implementację wyszukiwania, wykonując następujące kroki:

    1. Odbuduj projekt i rozpocznij debugowanie.

    2. W eksperymentalnym wystąpieniu programu Visual Studio otwórz ponownie okno narzędzia, wprowadź tekst wyszukiwania w oknie wyszukiwania i kliknij przycisk **ENTER**.

         Powinny pojawić się poprawne wyniki.

## <a name="to-customize-the-search-behavior"></a>Aby dostosować zachowanie wyszukiwania
 Zmieniając ustawienia wyszukiwania, można wprowadzić różne zmiany w sposobie wyświetlania formantu wyszukiwania i sposobu wyszukiwania. Można na przykład zmienić znak wodny (domyślny tekst wyświetlany w polu wyszukiwania), minimalną i maksymalną szerokość formantu wyszukiwania oraz informacje o tym, czy ma być wyświetlany pasek postępu. Możesz też zmienić punkt, w którym zaczynają się pojawiać wyniki wyszukiwania (na żądanie lub wyszukiwanie błyskawiczne) oraz czy chcesz wyświetlić listę terminów, dla których ostatnio wyszukiwano. Pełną listę ustawień można znaleźć <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource> w klasie.

1. W pliku* TestSearch.cs* dodaj do `TestSearch` klasy następujący kod. Ten kod umożliwia wyszukiwanie błyskawiczne zamiast wyszukiwania na żądanie (co oznacza, że użytkownik nie musi **klikać**enter). Kod zastępuje `ProvideSearchSettings` metodę w `TestSearch` klasie, która jest niezbędna do zmiany ustawień domyślnych.

    ```csharp
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)
    {
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchStartTypeProperty.Name,
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}
    ```

2. Przetestuj nowe ustawienie, przebudowując rozwiązanie i ponownie uruchamiając debuger.

     Wyniki wyszukiwania są wyświetlane za każdym razem, gdy wprowadzasz znak w polu wyszukiwania.

3. W `ProvideSearchSettings` metodzie dodaj następujący wiersz, który umożliwia wyświetlanie paska postępu.

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

     Aby pasek postępu był wyświetlany, należy podać postęp. Aby zgłosić postęp, odkomentuj `OnStartSearch` następujący `TestSearchTask` kod w metodzie klasy:

    ```csharp
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));
    ```

4. Aby spowolnić przetwarzanie na tyle, że pasek postępu jest `OnStartSearch` widoczny, `TestSearchTask` odkomentuj następujący wiersz w metodzie klasy:

    ```csharp
    System.Threading.Thread.Sleep(100);
    ```

5. Przetestuj nowe ustawienia, przebudowując rozwiązanie i rozpoczynając debugowanie.

     Pasek postępu pojawia się w oknie wyszukiwania (jako niebieska linia pod polem tekstowym wyszukiwania) za każdym razem, gdy wykonujesz wyszukiwanie.

## <a name="to-enable-users-to-refine-their-searches"></a>Aby umożliwić użytkownikom zawężenie wyszukiwania
 Można zezwolić użytkownikom na zawężenie wyszukiwania za pomocą opcji, takich jak **Dopasowanie sprawy** lub **Dopasuj całe słowo**. Opcje mogą być logiczne, które są wyświetlane jako pola wyboru lub polecenia, które są wyświetlane jako przyciski. W tym instruktażu utworzysz opcję logiczną.

1. W pliku *TestSearch.cs* dodaj następujący kod do `TestSearch` klasy. Kod zastępuje `SearchOptionsEnum` metodę, która umożliwia implementacji wyszukiwania wykryć, czy dana opcja jest wł., czy wyłączona. Kod w `SearchOptionsEnum` dodaje opcję, aby <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions> dopasować sprawę do wylicznika. Opcja dopasowania przypadku jest również dostępna `MatchCaseOption` jako właściwość.

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

2. W `TestSearchTask` klasie odkomentuj następujący `OnStartSearch` wiersz w metodzie:

    ```csharp
    matchCase = m_toolWindow.MatchCaseOption.Value;
    ```

3. Przetestuj opcję:

    1. Skompiluj projekt i rozpocznij debugowanie. Pojawi się eksperymentalne wystąpienie.

    2. W oknie narzędzia wybierz strzałkę w dół po prawej stronie pola tekstowego.

         Pojawi się pole wyboru **Dopasuj sprawę.**

    3. Zaznacz pole wyboru **Dopasuj sprawę,** a następnie wykonaj niektóre wyszukiwania.

## <a name="to-add-a-search-filter"></a>Aby dodać filtr wyszukiwania
 Można dodać filtry wyszukiwania, które umożliwiają użytkownikom zawężenie zestawu obiektów docelowych wyszukiwania. Na przykład można filtrować pliki w Eksploratorze plików według dat, w których zostały ostatnio zmodyfikowane, oraz ich rozszerzenia nazw plików. W tym instruktażu dodasz filtr tylko dla parzystych wierszy. Gdy użytkownik wybierze ten filtr, host wyszukiwania dodaje ciągi określone do kwerendy wyszukiwania. Następnie można zidentyfikować te ciągi wewnątrz metody wyszukiwania i odpowiednio filtrować obiekty docelowe wyszukiwania.

1. W pliku *TestSearch.cs* dodaj następujący kod do `TestSearch` klasy. Kod implementuje, `SearchFiltersEnum` dodając, <xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter> że określa, aby filtrować wyniki wyszukiwania, tak aby wyświetlane były tylko równe wiersze.

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

     Teraz formant wyszukiwania wyświetla `Search even lines only`filtr wyszukiwania . Gdy użytkownik wybierze filtr, `lines:"even"` ciąg pojawi się w polu wyszukiwania. Inne kryteria wyszukiwania mogą pojawić się w tym samym czasie co filtr. Ciągi wyszukiwania mogą pojawić się przed filtrem, po filtrze lub obu.

2. W pliku *TestSearch.cs* dodaj następujące metody do `TestSearchTask` klasy, która znajduje `TestSearch` się w klasie. Te metody `OnStartSearch` obsługują metodę, którą zmodyfikujesz w następnym kroku.

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

3. W `TestSearchTask` klasie zaktualizuj `OnStartSearch` metodę za pomocą następującego kodu. Ta zmiana aktualizuje kod do obsługi filtru.

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

5. Skompiluj projekt i rozpocznij debugowanie. W eksperymentalnym wystąpieniu programu Visual Studio otwórz okno narzędzia, a następnie wybierz strzałkę w dół w formancie wyszukiwania.

     Pole wyboru **Dopasuj sprawę** i wyświetlą tylko filtr **Wyszukaj w wierszach parzystych.**

6. Wybierz filtr.

     Pole wyszukiwania zawiera **wiersze:"parzyste"** i wyświetlane są następujące wyniki:

     2 dobre

     4 Dobry

     6 Do widzenia

7. Usuń `lines:"even"` z pola wyszukiwania, zaznacz pole wyboru **Dopasuj sprawę,** a następnie wprowadź `g` pole wyszukiwania.

     Pojawiają się następujące wyniki:

     1 przejdź

     2 dobre

     5 do widzenia

8. Wybierz znak X po prawej stronie pola wyszukiwania.

     Wyszukiwanie zostanie wyczyszczone, a oryginalna zawartość zostanie wyświetlona. Jednak pole wyboru **Dopasuj sprawę** jest nadal zaznaczone.
