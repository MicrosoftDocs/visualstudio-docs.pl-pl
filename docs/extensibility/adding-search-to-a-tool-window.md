---
title: Dodawanie wyszukiwania do okna narzędzi | Microsoft Docs
description: Dowiedz się, jak dodać funkcję wyszukiwania, w tym pole wyszukiwania, filtrowanie i wskaźnik postępu, do okna narzędzia w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 82176afaacae3b9f4553c8b1b5b41b9a4f10dace
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097555"
---
# <a name="add-search-to-a-tool-window"></a>Dodawanie wyszukiwania do okna narzędzi
Po utworzeniu lub zaktualizowaniu okna narzędzi w rozszerzeniu można dodać tę samą funkcję wyszukiwania, która pojawia się w innym miejscu w programie Visual Studio. Ta funkcja obejmuje następujące funkcje:

- Pole wyszukiwania, które zawsze znajduje się w niestandardowym obszarze paska narzędzi.

- Wskaźnik postępu, który jest nałożony w polu wyszukiwania.

- Możliwość wyświetlania wyników zaraz po wprowadzeniu każdego znaku (natychmiastowe wyszukiwanie) lub tylko po wybraniu klawisza **Enter** (wyszukiwanie na żądanie).

- Lista pokazująca warunki, dla których Przeszukiwano ostatnio.

- Możliwość filtrowania wyszukiwań według określonych pól lub aspektów celów wyszukiwania.

Postępując zgodnie z tym przewodnikiem, dowiesz się, jak wykonywać następujące zadania:

1. Utwórz projekt pakietu VSPackage.

2. Utwórz okno narzędzi, które zawiera element UserControl z polem tekstowym tylko do odczytu.

3. Dodaj pole wyszukiwania do okna narzędzi.

4. Dodaj implementację wyszukiwania.

5. Włącz natychmiastowe wyszukiwanie i wyświetlanie paska postępu.

6. Dodaj opcję **uwzględniania wielkości liter** .

7. Dodaj filtr **tylko linie wyszukiwania parzyste** .

## <a name="to-create-a-vsix-project"></a>Aby utworzyć projekt VSIX

1. Utwórz projekt VSIX o nazwie `TestToolWindowSearch` przy użyciu okna narzędzia o nazwie **TestSearch**. Jeśli potrzebujesz pomocy, zapoznaj się z tematem [Tworzenie rozszerzenia przy użyciu okna narzędzi](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="to-create-a-tool-window"></a>Aby utworzyć okno narzędzi

1. W `TestToolWindowSearch` projekcie Otwórz plik *TestSearchControl. XAML* .

2. Zastąp istniejący `<StackPanel>` blok następującym blokiem, który dodaje tylko <xref:System.Windows.Controls.TextBox> do odczytu <xref:System.Windows.Controls.UserControl> w oknie narzędzi.

    ```xaml
    <StackPanel Orientation="Vertical">
        <TextBox Name="resultsTextBox" Height="800.0"
            Width="800.0"
            IsReadOnly="True">
        </TextBox>
    </StackPanel>
    ```

3. W pliku *TestSearchControl. XAML. cs* Dodaj następującą dyrektywę using:

    ```csharp
    using System.Text;
    ```

4. Usuń `button1_Click()` metodę.

     W klasie **TestSearchControl** Dodaj następujący kod.

     Ten kod dodaje publiczną <xref:System.Windows.Controls.TextBox> Właściwość o nazwie **SearchResultsTextBox** i publiczną właściwość ciągu o nazwie **SearchContent**. W konstruktorze SearchResultsTextBox jest ustawiony na pole tekstowe, a SearchContent jest inicjowany do zestawu ciągów rozdzielanych znakami nowego wiersza. Zawartość pola tekstowego jest również inicjowana do zestawu ciągów.

     [!code-csharp[ToolWindowSearch#1](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs)]
     [!code-vb[ToolWindowSearch#1](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]

5. Skompiluj projekt i Rozpocznij debugowanie. Pojawia się eksperymentalne wystąpienie programu Visual Studio.

6. Na pasku menu wybierz opcję **Wyświetl**  >  **inne okna**  >  **TestSearch**.

     Zostanie wyświetlone okno narzędzia, ale formant wyszukiwania nie jest jeszcze wyświetlany.

## <a name="to-add-a-search-box-to-the-tool-window"></a>Aby dodać pole wyszukiwania do okna narzędzi

1. W pliku *TestSearch. cs* Dodaj następujący kod do `TestSearch` klasy. Kod zastępuje właściwość, <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> Aby metoda dostępu get zwracała wartość `true` .

     Aby włączyć wyszukiwanie, należy zastąpić <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> Właściwość. <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>Klasa implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> i udostępnia implementację domyślną, która nie umożliwia wyszukiwania.

    ```csharp
    public override bool SearchEnabled
    {
        get { return true; }
    }
    ```

2. Skompiluj projekt i Rozpocznij debugowanie. Zostanie wyświetlone wystąpienie eksperymentalne.

3. W eksperymentalnym wystąpieniu programu Visual Studio Otwórz **TestSearch**.

     W górnej części okna narzędzia kontrolka wyszukiwania pojawia się z **wyszukiwanym** znakiem wodnym i ikoną lupy. Jednak wyszukiwanie nie działa jeszcze, ponieważ proces wyszukiwania nie został zaimplementowany.

## <a name="to-add-the-search-implementation"></a>Aby dodać implementację wyszukiwania
 Po włączeniu wyszukiwania na <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> , jak w poprzedniej procedurze, okno narzędzia tworzy hosta wyszukiwania. Ten host konfiguruje procesy wyszukiwania, które są zawsze wykonywane w wątku w tle, i zarządza nimi. Ponieważ <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> Klasa zarządza tworzeniem hosta wyszukiwania i konfigurowaniem wyszukiwania, wystarczy utworzyć zadanie wyszukiwania i podać metodę wyszukiwania. Proces wyszukiwania odbywa się w wątku w tle, a wywołania kontrolki okna narzędzia pojawiają się w wątku interfejsu użytkownika. W związku z tym należy użyć metody [ThreadHelper. Invoke *](https://msdn.microsoft.com/data/ee197798(v=vs.85)) do zarządzania wszelkimi wywołaniami, które należy wykonać w celu przejmowania z kontrolką.

1. W pliku *TestSearch. cs* Dodaj następujące `using` dyrektywy:

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

2. W `TestSearch` klasie Dodaj następujący kod, który wykonuje następujące czynności:

    - Zastępuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> metodę, aby można było utworzyć zadanie wyszukiwania.

    - Zastępuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> metodę, aby przywrócić stan pola tekstowego. Ta metoda jest wywoływana, gdy użytkownik anuluje zadanie wyszukiwania, a użytkownik ustawia lub usuwa ustawienia opcji lub filtrów. Oba <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> są wywoływane w wątku interfejsu użytkownika. W związku z tym nie musisz uzyskiwać dostępu do pola tekstowego za pomocą metody [ThreadHelper. Invoke *](https://msdn.microsoft.com/data/ee197798(v=vs.85)) .

    - Tworzy klasę o nazwie, która `TestSearchTask` dziedziczy z <xref:Microsoft.VisualStudio.Shell.VsSearchTask> , która zapewnia domyślną implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask> .

         W programie `TestSearchTask` Konstruktor ustawia pole prywatne odwołujące się do okna narzędzi. Aby zapewnić metodę wyszukiwania, należy zastąpić <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A> metody i. <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A>Metoda polega na zaimplementowaniu procesu wyszukiwania. Ten proces obejmuje przeprowadzenie wyszukiwania, wyświetlenie wyników wyszukiwania w polu tekstowym i wywołanie implementacji klasy bazowej tej metody w celu zgłaszania, że wyszukiwanie zostało zakończone.

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

3. Przetestuj implementację wyszukiwania, wykonując następujące czynności:

    1. Skompiluj ponownie projekt i Rozpocznij debugowanie.

    2. W eksperymentalnym wystąpieniu programu Visual Studio, Otwórz ponownie okno narzędzia, wprowadź tekst wyszukiwania w oknie wyszukiwania, a następnie kliknij przycisk **Enter**.

         Powinny pojawić się poprawne wyniki.

## <a name="to-customize-the-search-behavior"></a>Aby dostosować zachowanie wyszukiwania
 Zmieniając ustawienia wyszukiwania, można wprowadzać różne zmiany w sposobie wyświetlania kontrolki wyszukiwania oraz sposobu, w jaki wyszukiwane jest wyszukiwanie. Na przykład można zmienić znak wodny (domyślny tekst wyświetlany w polu wyszukiwania), minimalną i maksymalną szerokość kontrolki wyszukiwania oraz określić, czy ma być pokazywany pasek postępu. Możesz również zmienić punkt, w którym wyniki wyszukiwania zaczynają się pojawiać (na żądanie lub natychmiastowe wyszukiwanie) i czy pokazywać listę warunków, dla których ostatnio Przeszukiwano. Pełną listę ustawień można znaleźć w <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource> klasie.

1. W pliku * TestSearch. cs * Dodaj następujący kod do `TestSearch` klasy. Ten kod umożliwia błyskawiczne wyszukiwanie zamiast wyszukiwania na żądanie (oznacza to, że użytkownik nie musi klikać klawisza **Enter**). Kod zastępuje `ProvideSearchSettings` metodę w `TestSearch` klasie, która jest niezbędna do zmiany ustawień domyślnych.

    ```csharp
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)
    {
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchStartTypeProperty.Name,
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}
    ```

2. Przetestuj nowe ustawienie, przebudując rozwiązanie i ponownie uruchamiając debuger.

     Wyniki wyszukiwania pojawiają się za każdym razem, gdy wprowadzasz znak w polu wyszukiwania.

3. W `ProvideSearchSettings` metodzie Dodaj następujący wiersz, który umożliwia wyświetlanie paska postępu.

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

     Aby pasek postępu pojawił się, należy zgłosić postęp. Aby zgłosić postęp, Usuń komentarz z poniższego kodu w `OnStartSearch` metodzie `TestSearchTask` klasy:

    ```csharp
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));
    ```

4. Aby wolne przetwarzanie było wystarczające, aby pasek postępu był widoczny, Usuń komentarz z następującego wiersza w `OnStartSearch` metodzie `TestSearchTask` klasy:

    ```csharp
    System.Threading.Thread.Sleep(100);
    ```

5. Przetestuj nowe ustawienia przez odbudowanie rozwiązania i rozpoczęcie debugowania.

     Pasek postępu pojawia się w oknie wyszukiwania (jako niebieska linia poniżej pola tekstowego wyszukiwania) przy każdym przeszukiwaniu.

## <a name="to-enable-users-to-refine-their-searches"></a>Aby umożliwić użytkownikom udoskonalenie wyszukiwania
 Możesz pozwolić użytkownikom na udoskonalenie wyszukiwania przy użyciu opcji takich jak **dopasowanie wielkości liter** lub **dopasowanie całego wyrazu**. Opcje mogą być wartością logiczną, która pojawia się jako pola wyboru lub polecenia, które są wyświetlane jako przyciski. W tym instruktażu utworzysz opcję logiczną.

1. W pliku *TestSearch. cs* Dodaj następujący kod do `TestSearch` klasy. Kod zastępuje `SearchOptionsEnum` metodę, która umożliwia implementacji wyszukiwania wykrywanie, czy dana opcja jest włączona czy wyłączona. Kod w `SearchOptionsEnum` dodaje opcję dopasowania wielkości liter do <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions> modułu wyliczającego. Opcja dopasowania wielkości liter jest również dostępna jako `MatchCaseOption` Właściwość.

    ```csharp
    private IVsEnumWindowSearchOptions m_optionsEnum;
    public override IVsEnumWindowSearchOptions SearchOptionsEnum
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

2. W `TestSearchTask` klasie Usuń komentarz z następującego wiersza w `OnStartSearch` metodzie:

    ```csharp
    matchCase = m_toolWindow.MatchCaseOption.Value;
    ```

3. Przetestuj opcję:

    1. Skompiluj projekt i Rozpocznij debugowanie. Zostanie wyświetlone wystąpienie eksperymentalne.

    2. W oknie Narzędzia wybierz strzałkę w dół znajdującą się po prawej stronie pola tekstowego.

         Zostanie wyświetlone pole wyboru **Uwzględnij wielkość liter** .

    3. Zaznacz pole wyboru **Uwzględnij wielkość liter** , a następnie wykonaj pewne wyszukiwania.

## <a name="to-add-a-search-filter"></a>Aby dodać filtr wyszukiwania
 Można dodać filtry wyszukiwania, które umożliwiają użytkownikom udoskonalenie zestawu celów wyszukiwania. Na przykład można filtrować pliki w Eksploratorze plików według dat, w których zostały ostatnio zmodyfikowane i ich rozszerzenia nazw plików. W tym instruktażu dodasz filtr tylko dla wierszy parzystych. Gdy użytkownik wybierze ten filtr, Host wyszukiwania dodaje ciągi określone w zapytaniu wyszukiwania. Następnie można zidentyfikować te ciągi wewnątrz metody wyszukiwania i odpowiednio odfiltrować cele wyszukiwania.

1. W pliku *TestSearch. cs* Dodaj następujący kod do `TestSearch` klasy. Kod implementuje `SearchFiltersEnum` przez dodanie elementu <xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter> , który określa, aby przefiltrować wyniki wyszukiwania, tak aby pojawiły się tylko parzyste wiersze.

    ```csharp
    public override IVsEnumWindowSearchFilters SearchFiltersEnum
    {
        get
        {
            List<IVsWindowSearchFilter> list = new List<IVsWindowSearchFilter>();
            list.Add(new WindowSearchSimpleFilter("Search even lines only", "Search even lines only", "lines", "even"));
            return new WindowSearchFilterEnumerator(list) as IVsEnumWindowSearchFilters;
        }
    }

    ```

     Teraz w kontrolce wyszukiwania zostanie wyświetlony filtr wyszukiwania `Search even lines only` . Gdy użytkownik wybierze filtr, ciąg `lines:"even"` pojawi się w polu wyszukiwania. Inne kryteria wyszukiwania mogą pojawiać się w tym samym czasie co filtr. Ciągi wyszukiwania mogą występować przed filtrem, po filtrowaniu lub obu.

2. W pliku *TestSearch. cs* Dodaj następujące metody do `TestSearchTask` klasy, która znajduje się w `TestSearch` klasie. Te metody obsługują `OnStartSearch` metodę, którą można zmodyfikować w następnym kroku.

    ```csharp
    private string RemoveFromString(string origString, string stringToRemove)
    {
        int index = origString.IndexOf(stringToRemove);
        if (index == -1)
            return origString;
        else 
             return (origString.Substring(0, index) + origString.Substring(index + stringToRemove.Length)).Trim();
    }

    private string[] GetEvenItems(string[] contentArr)
    {
        int length = contentArr.Length / 2;
        string[] evenContentArr = new string[length];

        int indexB = 0;
        for (int index = 1; index < contentArr.Length; index += 2)
        {
            evenContentArr[indexB] = contentArr[index];
            indexB++;
        }

        return evenContentArr;
    }
    ```

3. W `TestSearchTask` klasie należy zaktualizować `OnStartSearch` metodę przy użyciu następującego kodu. Ta zmiana aktualizuje kod obsługujący filtr.

    ```csharp
    protected override void OnStartSearch()
    {
        // Use the original content of the text box as the target of the search. 
        var separator = new string[] { Environment.NewLine };
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

5. Skompiluj projekt i Rozpocznij debugowanie. W eksperymentalnym wystąpieniu programu Visual Studio Otwórz okno narzędzia, a następnie wybierz strzałkę w dół w kontrolce wyszukiwanie.

     Zostanie wyświetlone pole wyboru **Uwzględnij wielkość liter** i filtr **tylko linie wyszukiwania parzyste** .

6. Wybierz filtr.

     Pole wyszukiwania zawiera **wiersze: "nawet"** i są wyświetlane następujące wyniki:

     2 dobre

     4 dobre

     6.

7. Usuń `lines:"even"` z pola wyszukiwania, zaznacz pole wyboru **Uwzględnij wielkość liter** , a następnie wprowadź `g` w polu wyszukiwania.

     Zostaną wyświetlone następujące wyniki:

     1 Przejdź

     2 dobre

     5.

8. Wybierz znak X z prawej strony pola wyszukiwania.

     Wyszukiwanie jest wyczyszczone i zostanie wyświetlona oryginalna zawartość. Jednak pole wyboru **Uwzględnij wielkość liter** nadal jest zaznaczone.
