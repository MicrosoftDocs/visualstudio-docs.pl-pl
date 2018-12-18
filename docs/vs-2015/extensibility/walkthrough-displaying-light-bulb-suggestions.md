---
title: 'Przewodnik: Wyświetlanie sugestie z żarówką | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a7e5bf7ad795615e70e990dd29c05f5efe3a1c78
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781104"
---
# <a name="walkthrough-displaying-light-bulb-suggestions"></a>Przewodnik: wyświetlanie sugestii „żarówka”
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ikony żarówek są ikony używane w edytorze programu Visual Studio, rozwinąć w celu wyświetlenia zestawem akcji, na przykład poprawki dotyczące problemów identyfikowane za pomocą analizatorów kodu wbudowanego lub refaktoryzacji kodu.  
  
 W edytorach Visual C# i Visual Basic można również użyć platformie kompilatora .NET ("Roslyn") do zapisu i tworzenia pakietów analizatorów własnego kodu z akcjami, które automatycznie wyświetlają żarówki. Aby uzyskać więcej informacji, zobacz:  
  
- [Instrukcje: Pisanie C# diagnostyki i poprawki kodu](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)  
  
- [Instrukcje: Pisanie diagnostyki programu Visual Basic i poprawki kodu](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)  
  
  Innych języków, takich jak C++ także zapewnić żarówki szybkich akcji, takich jak sugestię do tworzenia szkieletu stosowania tej funkcji.  
  
  Oto jak wygląda żarówki. W projekcie języka Visual Basic lub Visual C# czerwona fala pojawi się w obszarze Nazwa zmiennej, gdy jest on nieprawidłowy. Gdy wskaźnik myszy nad nieprawidłowy identyfikator żarówki jest wyświetlany obok kursora.  
  
  ![Ikona żarówki](../extensibility/media/lightbulb.png "żarówka")  
  
  Po kliknięciu strzałki w dół, żarówki zbiór sugerowanych akcji zostanie wyświetlona wraz z (wersja zapoznawcza) wybranej akcji. W tym przypadku pokazuje zmiany, które zostaną wprowadzone do kodu, jeśli wykonanie akcji.  
  
  ![żarówka — Podgląd](../extensibility/media/lightbulbpreview.png "LightBulbPreview")  
  
  Żarówki służy do zapewnienia sugerowanych akcji. Na przykład można dostarczyć działania, aby przenieść, otwierając nawiasy klamrowe do nowego wiersza lub przenieść je do końca poprzedniego wiersza. Następujące instruktaż przedstawia sposób tworzenia żarówki, która pojawia się na bieżącego słowa i ma dwa sugerowanych akcji: **Konwertuj na wielkie litery** i **konwersji na małe litery**.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Tworzenie projektu Framework (MEF) zarządzanych rozszerzeń  
  
1.  Utwórz projekt VSIX języka C#. (W **nowy projekt** okno dialogowe, wybierz opcję **Visual C# / rozszerzalności**, następnie **projekt VSIX**.) Nazwij rozwiązanie `LightBulbTest`.  
  
2.  Dodaj **klasyfikatora edytora** szablonu elementu projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Usuń istniejące pliki klasy.  
  
4.  Dodaj następujące odwołanie do projektu i ustaw **Kopiuj lokalnie** do `False`:  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
5.  Dodaj nowy plik klasy i nadaj mu nazwę **LightBulbTest**.  
  
6.  Dodaj następujące instrukcje using:  
  
    ```csharp  
    using System;  
    using System.Linq;  
    using System.Collections.Generic;  
    using System.Threading.Tasks;  
    using Microsoft.VisualStudio.Language.Intellisense;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Text.Operations;  
    using Microsoft.VisualStudio.Utilities;  
    using System.ComponentModel.Composition;  
    using System.Threading;  
  
    ```  
  
## <a name="implementing-the-light-bulb-source-provider"></a>Implementowanie dostawcy źródła żarówka  
  
1.  W pliku klasy LightBulbTest.cs Usuń klasy LightBulbTest. Dodaj klasę o nazwie **TestSuggestedActionsSourceProvider** implementującej <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>. Wyeksportuj go z nazwą **testu zalecane czynności** i <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> z "text".  
  
    ```csharp  
    [Export(typeof(ISuggestedActionsSourceProvider))]  
    [Name("Test Suggested Actions")]  
    [ContentType("text")]  
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider  
    ```  
  
2.  Wewnątrz klasy dostawcy źródła, należy zaimportować <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> i dodaj ją jako właściwość.  
  
    ```csharp  
    [Import(typeof(ITextStructureNavigatorSelectorService))]  
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }  
    ```  
  
3.  Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> metodę, aby zwrócić <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> obiektu. Omówimy źródła w następnej sekcji.  
  
    ```csharp  
    public ISuggestedActionsSource CreateSuggestedActionsSource(ITextView textView, ITextBuffer textBuffer)  
    {  
        if (textBuffer == null && textView == null)  
        {  
            return null;  
        }  
        return new TestSuggestedActionsSource(this, textView, textBuffer);  
    }  
    ```  
  
## <a name="implementing-the-isuggestedactionsource"></a>Implementowanie ISuggestedActionSource  
 Źródło sugerowanej akcji jest odpowiedzialny za zbieranie zbiór sugerowane akcje i dodawanie ich w odpowiednim kontekście. W tym przypadku jest bieżącego słowa w kontekście i sugerowane akcje są **UpperCaseSuggestedAction** i **LowerCaseSuggestedAction**, które omówimy w poniższej sekcji.  
  
1.  Dodaj klasę **TestSuggestedActionsSource** implementującej <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.  
  
    ```csharp  
    internal class TestSuggestedActionsSource : ISuggestedActionsSource  
    ```  
  
2.  Dostawca źródła sugerowanej akcji, bufor tekstowy i widoku tekstu, należy dodać prywatnego pola tylko do odczytu.  
  
    ```csharp  
    private readonly TestSuggestedActionsSourceProvider m_factory;  
    private readonly ITextBuffer m_textBuffer;  
    private readonly ITextView m_textView;  
    ```  
  
3.  Dodaj Konstruktor, który ustawia pól prywatnych.  
  
    ```csharp  
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)  
    {  
        m_factory = testSuggestedActionsSourceProvider;  
        m_textBuffer = textBuffer;  
        m_textView = textView;  
    }  
    ```  
  
4.  Dodaj metody prywatnej, która zwraca wyrazu, który jest obecnie pod kursorem. Następującą metodę wyglądu w bieżącej lokalizacji kursora i prosi Nawigator struktury tekstu dla zakresu programu word. Jeśli kursor znajduje się na słowo, <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> jest zwracana w parametrze wyjściowym; w przeciwnym razie `out` parametr jest `null` a metoda zwraca `false`.  
  
    ```csharp  
    private bool TryGetWordUnderCaret(out TextExtent wordExtent)  
    {  
        ITextCaret caret = m_textView.Caret;  
        SnapshotPoint point;  
  
        if (caret.Position.BufferPosition > 0)  
        {  
            point = caret.Position.BufferPosition - 1;  
        }  
        else  
        {  
            wordExtent = default(TextExtent);  
            return false;  
        }  
  
        ITextStructureNavigator navigator = m_factory.NavigatorService.GetTextStructureNavigator(m_textBuffer);  
  
        wordExtent = navigator.GetExtentOfWord(point);  
        return true;  
    }  
    ```  
  
5.  Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A> metody. Edytor wywołuje tę metodę, aby dowiedzieć się, czy mają być wyświetlane ikony żarówki. To wywołanie wykonano bardzo często, na przykład zawsze wtedy, gdy kursor przesuwa się w jednym wierszu do innego lub wskaźnika myszy nad wężyk błędu. Jest asynchroniczne, aby umożliwić innych operacji interfejsu użytkownika do wykonania, gdy ta metoda działa. W większości przypadków ta metoda musi wykonać niektóre analizy i analizy bieżący wiersz więc przetwarzania może trochę potrwać.  
  
     W naszej implementacji asynchronicznie pobiera <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> i określa, czy zakres jest istotne, czyli czy zawiera on tekst innym niż spacja.  
  
    ```csharp  
    public Task<bool> HasSuggestedActionsAsync(ISuggestedActionCategorySet requestedActionCategories, SnapshotSpan range, CancellationToken cancellationToken)  
    {  
        return Task.Factory.StartNew(() =>  
        {  
            TextExtent extent;  
            if (TryGetWordUnderCaret(out extent))  
            {  
                // don't display the action if the extent has whitespace  
                return extent.IsSignificant;  
              }  
            return false;  
        });  
    }  
    ```  
  
6.  Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> metody, która zwraca tablicę <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> obiektów, które zawierają różne <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> obiektów. Ta metoda jest wywoływana, gdy żarówki jest rozwinięty.  
  
    > [!WARNING]
    >  Upewnij się, że implementacje `HasSuggestedActionsAsync()` i `GetSuggestedActions()` są spójne; który jest, jeśli `HasSuggestedActionsAsync()` zwraca `true`, następnie `GetSuggestedActions()` powinny mieć pewne działania, aby wyświetlić. W wielu przypadkach `HasSuggestedActionsAsync()` jest wywoływana tuż przed `GetSuggestedActions()`, ale nie zawsze jest to wymagane. Na przykład, jeśli użytkownik wywoła akcje żarówki, naciskając klawisz (CTRL +.) tylko `GetSuggestedActions()` jest wywoływana.  
  
    ```csharp  
    public IEnumerable<SuggestedActionSet> GetSuggestedActions(ISuggestedActionCategorySet requestedActionCategories, SnapshotSpan range, CancellationToken cancellationToken)  
    {  
        TextExtent extent;  
        if (TryGetWordUnderCaret(out extent) && extent.IsSignificant)  
        {  
            ITrackingSpan trackingSpan = range.Snapshot.CreateTrackingSpan(extent.Span, SpanTrackingMode.EdgeInclusive);  
            var upperAction = new UpperCaseSuggestedAction(trackingSpan);  
            var lowerAction = new LowerCaseSuggestedAction(trackingSpan);  
            return new SuggestedActionSet[] { new SuggestedActionSet(new ISuggestedAction[] { upperAction, lowerAction }) };  
        }  
        return Enumerable.Empty<SuggestedActionSet>();  
    }   
    ```  
  
7.  Zdefiniuj `SuggestedActionsChanged` zdarzeń.  
  
    ```csharp  
    public event EventHandler<EventArgs> SuggestedActionsChanged;  
    ```  
  
8.  Aby wykonać wdrożenia, należy dodać implementacje dla `Dispose()` i `TryGetTelemetryId()` metody. Nie chcemy czy telemetrii i zwraca wartość false, więc tylko pusta wartość identyfikatora GUID.  
  
    ```csharp  
    public void Dispose()  
    {  
    }  
  
    public bool TryGetTelemetryId(out Guid telemetryId)  
    {  
        // This is a sample provider and doesn't participate in LightBulb telemetry  
        telemetryId = Guid.Empty;  
        return false;  
    }  
    ```  
  
## <a name="implementing-light-bulb-actions"></a>Implementowanie akcji żarówka  
  
1.  W projekcie Dodaj odwołanie do Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll i ustaw **Kopiuj lokalnie** do `False`.  
  
2.  Utwórz dwie klasy o nazwie pierwszy `UpperCaseSuggestedAction` i druga o nazwie `LowerCaseSuggestedAction`. Zarówno klasy implementować <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>.  
  
    ```csharp  
    internal class UpperCaseSuggestedAction : ISuggestedAction   
    internal class LowerCaseSuggestedAction : ISuggestedAction  
    ```  
  
     Obie klasy są podobne, z tą różnicą, że jeden wywołuje <xref:System.String.ToUpper%2A> i inne wywołania <xref:System.String.ToLower%2A>. W poniższych krokach opisano tylko klasy akcji wielkie litery, ale musi implementować zarówno klasy. Wykonaj kroki wykonania akcji wielkie litery jako wzorzec do wykonywania akcji małe litery.  
  
3.  Dodaj następujące instrukcje using dla tych klas:  
  
    ```csharp  
    using Microsoft.VisualStudio.Imaging.Interop;  
    using System.Windows;  
    using System.Windows.Controls;  
    using System.Windows.Documents;  
    using System.Windows.Media;  
  
    ```  
  
4.  Zadeklaruj zestaw pól prywatnych.  
  
    ```csharp  
    private ITrackingSpan m_span;  
    private string m_upper;  
    private string m_display;  
    private ITextSnapshot m_snapshot;  
    ```  
  
5.  Dodaj Konstruktor, który ustawia pola.  
  
    ```csharp  
    public UpperCaseSuggestedAction(ITrackingSpan span)  
    {  
        m_span = span;  
        m_snapshot = span.TextBuffer.CurrentSnapshot;  
        m_upper = span.GetText(m_snapshot).ToUpper();  
        m_display = string.Format("Convert '{0}' to upper case", span.GetText(m_snapshot));  
    }  
    ```  
  
6.  Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A> metodę, tak że Wyświetla podgląd akcji.  
  
    ```csharp  
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)  
    {  
        var textBlock = new TextBlock();  
        textBlock.Padding = new Thickness(5);  
        textBlock.Inlines.Add(new Run() { Text = m_upper });  
        return Task.FromResult<object>(textBlock);  
    }  
    ```  
  
7.  Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A> metodę, tak że zwraca pustą <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> wyliczenia.  
  
    ```csharp  
    public Task<IEnumerable<SuggestedActionSet>> GetActionSetsAsync(CancellationToken cancellationToken)  
    {  
        return Task.FromResult<IEnumerable<SuggestedActionSet>>(null);  
    }  
    ```  
  
8.  Implementuje właściwości w następujący sposób.  
  
    ```csharp  
    public bool HasActionSets  
    {  
        get { return false; }  
    }  
    public string DisplayText  
    {  
        get { return m_display; }  
    }  
    public ImageMoniker IconMoniker  
    {  
       get { return default(ImageMoniker); }  
    }  
    public string IconAutomationText  
    {  
        get  
        {  
            return null;  
        }  
    }  
    public string InputGestureText  
    {  
        get  
        {  
            return null;  
        }  
    }  
    public bool HasPreview  
    {  
        get { return true; }  
    }  
    ```  
  
9. Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A> metody, zastępując tekst w zakresie równoważnik wielkie litery.  
  
    ```csharp  
    public void Invoke(CancellationToken cancellationToken)  
    {  
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);  
    }  
    ```  
  
    > [!WARNING]
    >  Akcję żarówki **Invoke** metoda nie powinna się wyświetlić interfejs użytkownika.  Jeśli akcji wyświetlić nowy interfejs użytkownika (na przykład (wersja zapoznawcza) lub wyboru okna dialogowego), nie są wyświetlane interfejsu użytkownika bezpośrednio z poziomu **Invoke** metody, ale zamiast tego zaplanować, aby wyświetlić interfejs użytkownika po powrocie z **Invoke**.  
  
10. Aby wykonać wdrożenia, należy dodać `Dispose()` i `TryGetTelemetryId()` metody.  
  
    ```csharp  
    public void Dispose()  
    {  
    }  
  
    public bool TryGetTelemetryId(out Guid telemetryId)  
    {  
        // This is a sample action and doesn't participate in LightBulb telemetry  
        telemetryId = Guid.Empty;  
        return false;  
    }  
    ```  
  
11. Nie należy zapominać zrobić to samo `LowerCaseSuggestedAction` zmiana wyświetlanie tekstu w "Konwertuj"{0}"na małe litery", a następnie wywołać <xref:System.String.ToUpper%2A> do <xref:System.String.ToLower%2A>.  
  
## <a name="building-and-testing-the-code"></a>Tworzenie i testowanie kodu  
 Aby przetestować ten kod, Kompiluj rozwiązanie LightBulbTest, a następnie uruchomić go w doświadczalnym wystąpieniu.  
  
1.  Skompiluj rozwiązanie.  
  
2.  Po uruchomieniu tego projektu w debugerze drugiego wystąpienia programu Visual Studio jest uruchomiony.  
  
3.  Utwórz plik tekstowy i wpisz jakiś tekst. Powinien zostać wyświetlony żarówki po lewej stronie tekstu.  
  
     ![Testowanie żarówki](../extensibility/media/testlightbulb.png "TestLIghtBulb")  
  
4.  Wskaż żarówki. Powinien zostać wyświetlony strzałkę w dół.  
  
5.  Po kliknięciu ikony żarówki, dwie akcje sugerowane powinien zostać wyświetlony wraz z wersji zapoznawczej wybranej akcji.  
  
     ![Testowanie żarówki, rozwinięte](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")  
  
6.  Jeśli klikniesz pierwszą akcją, cały tekst w bieżącego słowa powinny być konwertowane na wielkie litery. Jeśli klikniesz drugiej akcji, cały tekst powinny być konwertowane na małe litery.

