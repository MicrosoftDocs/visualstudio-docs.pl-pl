---
title: 'Przewodnik: Wyświetlanie sugestie z żarówką | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d0799bdff6957e811c365fe153a722d25e306366
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60086679"
---
# <a name="walkthrough-display-light-bulb-suggestions"></a>Przewodnik: Wyświetl sugestie z żarówką
Ikony żarówek są ikony w edytorze programu Visual Studio, które rozwinąć w celu wyświetlenia zestawem akcji, na przykład poprawki dla problemów identyfikowane za pomocą analizatorów kodu wbudowanego lub refaktoryzacji kodu.

 W edytorach Visual C# i Visual Basic można również użyć platformie kompilatora .NET ("Roslyn") do zapisu i tworzenia pakietów analizatorów własnego kodu z akcjami, które automatycznie wyświetlają żarówki. Aby uzyskać więcej informacji, zobacz:

- [Instrukcje: Zapis C# diagnostycznych i poprawki kodu](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)

- [Instrukcje: Zapis diagnostyczne w Visual Basic i poprawki kodu](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)

  Innych języków, takich jak C++ także zapewnić żarówki szybkich akcji, takich jak sugestię do tworzenia szkieletu stosowania tej funkcji.

  Oto jak wygląda żarówki. W projekcie języka Visual Basic lub Visual C# czerwona fala pojawi się w obszarze Nazwa zmiennej, gdy jest on nieprawidłowy. Jeśli przesuniesz wskaźnik myszy nad nieprawidłowy identyfikator, żarówka pojawia się obok znajduje się kursor.

  ![Ikona żarówki](../extensibility/media/lightbulb.png "żarówka")

  Po kliknięciu strzałki w dół, żarówki, zbiór sugerowanych akcji zostanie wyświetlony wraz z (wersja zapoznawcza) wybranej akcji. W tym przypadku pokazuje zmiany, które zostały wprowadzone do kodu, jeśli wykonanie akcji.

  ![żarówka — Podgląd](../extensibility/media/lightbulbpreview.png "LightBulbPreview")

  Żarówki służy do zapewnienia sugerowanych akcji. Na przykład można dostarczyć działania, aby przenieść, otwierając nawiasy klamrowe do nowego wiersza lub przenieść je do końca poprzedniego wiersza. Następujące instruktaż przedstawia sposób tworzenia żarówki, która pojawia się na bieżącego słowa i ma dwa sugerowanych akcji: **Konwertuj na wielkie litery** i **konwersji na małe litery**.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie instaluj programu Visual Studio SDK z Centrum pobierania. Został on uwzględniony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalacji programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Utwórz projekt Managed Extensibility Framework (MEF)

1. Utwórz projekt VSIX języka C#. (W **nowy projekt** okno dialogowe, wybierz opcję **Visual C# / rozszerzalności**, następnie **projekt VSIX**.) Nazwij rozwiązanie `LightBulbTest`.

2. Dodaj **klasyfikatora edytora** szablonu elementu projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Usuń istniejące pliki klasy.

4. Dodaj następujące odwołanie do projektu i ustaw **Kopiuj lokalnie** do `False`:

     *Microsoft.VisualStudio.Language.Intellisense*

5. Dodaj nowy plik klasy i nadaj mu nazwę **LightBulbTest**.

6. Dodaj następujące instrukcje using:

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

## <a name="implement-the-light-bulb-source-provider"></a>Implementowanie dostawcy źródła żarówka

1. W *LightBulbTest.cs* klasy pliku, usunięcia klasy LightBulbTest. Dodaj klasę o nazwie **TestSuggestedActionsSourceProvider** implementującej <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>. Wyeksportuj go z nazwą **testu zalecane czynności** i <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> z "text".

    ```csharp
    [Export(typeof(ISuggestedActionsSourceProvider))]
    [Name("Test Suggested Actions")]
    [ContentType("text")]
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider
    ```

2. Wewnątrz klasy dostawcy źródła, należy zaimportować <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> i dodaj ją jako właściwość.

    ```csharp
    [Import(typeof(ITextStructureNavigatorSelectorService))]
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }
    ```

3. Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> metodę, aby zwrócić <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> obiektu. Źródło jest omówiona w następnej sekcji.

    ```csharp
    public ISuggestedActionsSource CreateSuggestedActionsSource(ITextView textView, ITextBuffer textBuffer)
    {
        if (textBuffer == null || textView == null)
        {
            return null;
        }
        return new TestSuggestedActionsSource(this, textView, textBuffer);
    }
    ```

## <a name="implement-the-isuggestedactionsource"></a>Implementowanie ISuggestedActionSource
 Źródło sugerowanej akcji jest odpowiedzialny za zbieranie zbiór sugerowane akcje i dodawanie ich w odpowiednim kontekście. W takim przypadku kontekst jest bieżącego słowa i sugerowane akcje są **UpperCaseSuggestedAction** i **LowerCaseSuggestedAction**, która została omówiona w następnej sekcji.

1. Dodaj klasę **TestSuggestedActionsSource** implementującej <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.

    ```csharp
    internal class TestSuggestedActionsSource : ISuggestedActionsSource
    ```

2. Dodaj pola prywatne, tylko do odczytu dla dostawcy źródła sugerowanej akcji, bufor tekstowy i widoku tekstu.

    ```csharp
    private readonly TestSuggestedActionsSourceProvider m_factory;
    private readonly ITextBuffer m_textBuffer;
    private readonly ITextView m_textView;
    ```

3. Dodaj Konstruktor, który ustawia pól prywatnych.

    ```csharp
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)
    {
        m_factory = testSuggestedActionsSourceProvider;
        m_textBuffer = textBuffer;
        m_textView = textView;
    }
    ```

4. Dodaj metody prywatnej, która zwraca wyrazu, który jest obecnie pod kursorem. Następującą metodę wyglądu w bieżącej lokalizacji kursora i prosi Nawigator struktury tekstu dla zakresu programu word. Jeśli kursor znajduje się na słowo, <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> jest zwracany w parametrze wyjściowym; w przeciwnym razie `out` parametr jest `null` a metoda zwraca `false`.

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

5. Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A> metody. Edytor wywołuje tę metodę, aby dowiedzieć się, czy mają być wyświetlane ikony żarówki. To wywołanie wykonano często, na przykład zawsze wtedy, gdy kursor przesuwa się w jednym wierszu do innego lub wskaźnika myszy nad wężyk błędu. Jest asynchroniczne, aby umożliwić innych operacji interfejsu użytkownika do wykonania, gdy ta metoda działa. W większości przypadków ta metoda musi wykonać niektóre analizy i analizy bieżący wiersz, więc przetwarzanie może zająć trochę czasu.

     W tej implementacji asynchronicznie pobiera <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> i określa, czy zakres jest znaczący, tak jak, czy ma jakiś tekst innym niż spacja.

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

6. Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> metody, która zwraca tablicę <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> obiektów, które zawierają różne <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> obiektów. Ta metoda jest wywoływana, gdy żarówki jest rozwinięty.

    > [!WARNING]
    >  Upewnij się, że implementacje `HasSuggestedActionsAsync()` i `GetSuggestedActions()` są spójne; który jest, jeśli `HasSuggestedActionsAsync()` zwraca `true`, następnie `GetSuggestedActions()` powinny mieć pewne działania, aby wyświetlić. W wielu przypadkach `HasSuggestedActionsAsync()` jest wywoływana tuż przed `GetSuggestedActions()`, ale nie zawsze jest to wymagane. Na przykład, jeśli użytkownik wywoła akcje żarówki, naciskając klawisz (**CTRL +** .) tylko `GetSuggestedActions()` jest wywoływana.

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

7. Zdefiniuj `SuggestedActionsChanged` zdarzeń.

    ```csharp
    public event EventHandler<EventArgs> SuggestedActionsChanged;
    ```

8. Aby wykonać wdrożenia, należy dodać implementacje dla `Dispose()` i `TryGetTelemetryId()` metody. Nie chcesz zrobić telemetrii, więc Zwróć `false` i wartość identyfikatora GUID `Empty`.

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

## <a name="implement-light-bulb-actions"></a>Akcje żarówka wdrożenie

1. W projekcie Dodaj odwołanie do *Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll* i ustaw **Kopiuj lokalnie** do `False`.

2. Utwórz dwie klasy o nazwie pierwszy `UpperCaseSuggestedAction` i druga o nazwie `LowerCaseSuggestedAction`. Zarówno klasy implementować <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>.

    ```csharp
    internal class UpperCaseSuggestedAction : ISuggestedAction
    internal class LowerCaseSuggestedAction : ISuggestedAction
    ```

     Obie klasy są podobne, z tą różnicą, że jeden wywołuje <xref:System.String.ToUpper%2A> i inne wywołania <xref:System.String.ToLower%2A>. W poniższych krokach opisano tylko klasy akcji wielkie litery, ale musi implementować zarówno klasy. Wykonaj kroki wykonania akcji wielkie litery jako wzorzec do wykonywania akcji małe litery.

3. Dodaj następujące instrukcje using dla tych klas:

    ```csharp
    using Microsoft.VisualStudio.Imaging.Interop;
    using System.Windows;
    using System.Windows.Controls;
    using System.Windows.Documents;
    using System.Windows.Media;

    ```

4. Zadeklaruj zestaw pól prywatnych.

    ```csharp
    private ITrackingSpan m_span;
    private string m_upper;
    private string m_display;
    private ITextSnapshot m_snapshot;
    ```

5. Dodaj Konstruktor, który ustawia pola.

    ```csharp
    public UpperCaseSuggestedAction(ITrackingSpan span)
    {
        m_span = span;
        m_snapshot = span.TextBuffer.CurrentSnapshot;
        m_upper = span.GetText(m_snapshot).ToUpper();
        m_display = string.Format("Convert '{0}' to upper case", span.GetText(m_snapshot));
    }
    ```

6. Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A> metodę, tak że Wyświetla podgląd akcji.

    ```csharp
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)
    {
        var textBlock = new TextBlock();
        textBlock.Padding = new Thickness(5);
        textBlock.Inlines.Add(new Run() { Text = m_upper });
        return Task.FromResult<object>(textBlock);
    }
    ```

7. Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A> metodę, tak że zwraca pustą <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> wyliczenia.

    ```csharp
    public Task<IEnumerable<SuggestedActionSet>> GetActionSetsAsync(CancellationToken cancellationToken)
    {
        return Task.FromResult<IEnumerable<SuggestedActionSet>>(null);
    }
    ```

8. Implementuje właściwości w następujący sposób.

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
    >  Akcję żarówki **Invoke** metoda nie powinna się wyświetlić interfejs użytkownika. Jeśli akcji wyświetlić nowy interfejs użytkownika (na przykład (wersja zapoznawcza) lub wyboru okna dialogowego), nie są wyświetlane interfejsu użytkownika bezpośrednio z poziomu **Invoke** metody, ale zamiast tego zaplanować, aby wyświetlić interfejs użytkownika po powrocie z **Invoke**.

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

## <a name="build-and-test-the-code"></a>Tworzenie i testowanie kodu
 Aby przetestować ten kod, Kompiluj rozwiązanie LightBulbTest, a następnie uruchomić go w doświadczalnym wystąpieniu.

1. Skompiluj rozwiązanie.

2. Po uruchomieniu tego projektu w debugerze, drugie wystąpienie programu Visual Studio został uruchomiony.

3. Utwórz plik tekstowy i wpisz jakiś tekst. Powinien zostać wyświetlony żarówki po lewej stronie tekstu.

     ![Testowanie żarówki](../extensibility/media/testlightbulb.png "TestLIghtBulb")

4. Wskaż żarówki. Powinien zostać wyświetlony strzałkę w dół.

5. Po kliknięciu ikony żarówki, dwie akcje sugerowane powinien być wyświetlany wraz z wersji zapoznawczej wybranej akcji.

     ![Testowanie żarówki, rozwinięte](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")

6. Jeśli klikniesz pierwszą akcją, cały tekst w bieżącego słowa powinny być konwertowane na wielkie litery. Jeśli klikniesz drugiej akcji, cały tekst powinny być konwertowane na małe.
