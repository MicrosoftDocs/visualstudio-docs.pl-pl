---
title: 'Przewodnik: wyświetlanie sugestii żarówki | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 153eda065b9a6e845a39c35aaae34bbe1745f7a8
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905004"
---
# <a name="walkthrough-display-light-bulb-suggestions"></a>Przewodnik: wyświetlanie sugestii żarówki
Żarówki są ikonami w edytorze programu Visual Studio, które rozszerzają się, aby wyświetlić zestaw akcji, na przykład poprawki dotyczące problemów zidentyfikowanych przez wbudowane analizatory kodu lub refaktoryzacji kodu.

 W edytorach Visual C# i Visual Basic można także użyć .NET Compiler Platform ("Roslyn"), aby napisać i spakować własne analizatory kodu z akcjami, które automatycznie wyświetlają żarówki. Aby uzyskać więcej informacji, zobacz:

- [Instrukcje: pisanie diagnostyki i naprawa kodu w języku C#](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)

- [Instrukcje: pisanie Visual Basic diagnostyki i poprawiania kodu](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)

  Inne języki, takie jak C++, udostępniają również żarówki dla niektórych szybkich akcji, takich jak, sugestii do tworzenia implementacji zastępczej tej funkcji.

  Oto, jak wygląda żarówka. W projekcie Visual Basic lub Visual C# czerwony zygzak pojawia się pod nazwą zmiennej, gdy jest nieprawidłowy. Jeśli wskaźnik myszy znajduje się nad nieprawidłowym identyfikatorem, żarówka zostanie wyświetlona blisko kursora.

  ![Żarówka](../extensibility/media/lightbulb.png "Żarówki")

  Po kliknięciu strzałki w dół przez żarówkę zostanie wyświetlony zestaw sugerowanych akcji wraz z podglądem wybranej akcji. W tym przypadku pokazuje zmiany wprowadzone w kodzie w przypadku wykonania akcji.

  ![Żarówka — Podgląd](../extensibility/media/lightbulbpreview.png "LightBulbPreview")

  Możesz użyć żarówek, aby zapewnić własne sugerowane działania. Można na przykład udostępnić akcje przenoszenia otwierającego nawiasu klamrowego do nowego wiersza lub przenieść je na koniec poprzedniego wiersza. Poniższy przewodnik przedstawia sposób tworzenia żarówki, która pojawia się w bieżącym wyrazie i ma dwie sugerowane akcje: **Konwertuj na wielkie litery** i **Konwertuj na małe litery**.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dołączana jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Tworzenie projektu Managed Extensibility Framework (MEF)

1. Utwórz projekt VSIX języka C#. (W oknie dialogowym **Nowy projekt** wybierz pozycję **Visual C#/rozszerzalność**, a następnie **Projekt VSIX**). Nadaj nazwę rozwiązanie `LightBulbTest` .

2. Dodaj szablon elementu **klasyfikatora edytora** do projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Usuń istniejące pliki klas.

4. Dodaj następujące odwołanie do projektu i ustaw wartość **kopiowania lokalnego** na `False` :

     *Microsoft. VisualStudio. Language. IntelliSense*

5. Dodaj nowy plik klasy i nadaj mu nazwę **LightBulbTest**.

6. Dodaj następujące dyrektywy using:

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

## <a name="implement-the-light-bulb-source-provider"></a>Implementowanie dostawcy źródła żarówki

1. W pliku klasy *LightBulbTest.cs* Usuń klasę LightBulbTest. Dodaj klasę o nazwie **TestSuggestedActionsSourceProvider** , która implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider> . Wyeksportuj go przy użyciu nazwy **sugerowanych akcji testowych** i elementu <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text".

    ```csharp
    [Export(typeof(ISuggestedActionsSourceProvider))]
    [Name("Test Suggested Actions")]
    [ContentType("text")]
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider
    ```

2. W klasie dostawcy źródłowego zaimportuj <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> i Dodaj ją jako właściwość.

    ```csharp
    [Import(typeof(ITextStructureNavigatorSelectorService))]
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }
    ```

3. Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> metodę, aby zwrócić <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> obiekt. Źródło zostało omówione w następnej sekcji.

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
 Sugerowane Źródło akcji jest odpowiedzialne za gromadzenie zestawu sugerowanych akcji i dodawanie ich w odpowiednim kontekście. W takim przypadku kontekst jest bieżącym słowem, a sugerowane akcje to **UpperCaseSuggestedAction** i **LowerCaseSuggestedAction**, które omówiono w poniższej sekcji.

1. Dodaj klasę **TestSuggestedActionsSource** implementującą <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> .

    ```csharp
    internal class TestSuggestedActionsSource : ISuggestedActionsSource
    ```

2. Dodaj prywatne pola tylko do odczytu dla sugerowanego dostawcy źródła akcji, buforu tekstu i widoku tekstu.

    ```csharp
    private readonly TestSuggestedActionsSourceProvider m_factory;
    private readonly ITextBuffer m_textBuffer;
    private readonly ITextView m_textView;
    ```

3. Dodaj konstruktora, który ustawia pola prywatne.

    ```csharp
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)
    {
        m_factory = testSuggestedActionsSourceProvider;
        m_textBuffer = textBuffer;
        m_textView = textView;
    }
    ```

4. Dodaj prywatną metodę, która zwraca wyraz, który jest aktualnie pod kursorem. Poniższa metoda sprawdza bieżącą lokalizację kursora i prosi o nawigatora struktury tekstu w zakresie wyrazu. Jeśli kursor znajduje się w wyrazie, <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> jest zwracany w parametrze out; w przeciwnym razie `out` parametr jest `null` i zwraca metodę `false` .

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

5. Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A> metodę. Edytor wywołuje tę metodę, aby dowiedzieć się, czy ma być wyświetlana żarówka. To wywołanie jest często nawiązywane, na przykład za każdym razem, gdy kursor przesunie się z jednego wiersza do drugiego lub gdy wskaźnik myszy przesuwa się nad błędem. Jest ona asynchroniczna, aby umożliwić wykonywanie innych operacji interfejsu użytkownika, gdy ta metoda działa. W większości przypadków ta metoda musi wykonać analizę i analizę bieżącego wiersza, dzięki czemu przetwarzanie może zająć trochę czasu.

     W tej implementacji asynchronicznie pobiera <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> i określa, czy zakres jest znaczący, jak w, czy ma jakiś tekst inny niż odstęp.

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

6. Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> metodę, która zwraca tablicę <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> obiektów, które zawierają różne <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> obiekty. Ta metoda jest wywoływana, gdy żarówka jest rozwinięta.

    > [!WARNING]
    > Należy upewnić się, że implementacje `HasSuggestedActionsAsync()` i `GetSuggestedActions()` są spójne; oznacza to, że w przypadku `HasSuggestedActionsAsync()` powracania `true` `GetSuggestedActions()` powinno być wyświetlane pewne akcje. W wielu przypadkach `HasSuggestedActionsAsync()` jest wywoływana tuż przed `GetSuggestedActions()` , ale nie zawsze jest to przypadek. Na przykład, jeśli użytkownik wywołuje akcje żarówki przez naciśnięcie klawisza (**Ctrl +** .) `GetSuggestedActions()` jest wywoływana tylko.

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

7. Zdefiniuj `SuggestedActionsChanged` zdarzenie.

    ```csharp
    public event EventHandler<EventArgs> SuggestedActionsChanged;
    ```

8. Aby ukończyć implementację, Dodaj implementacje dla `Dispose()` `TryGetTelemetryId()` metod i. Nie chcesz robić danych telemetrycznych, więc po prostu zwróć `false` i ustaw identyfikator GUID na `Empty` .

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

## <a name="implement-light-bulb-actions"></a>Implementuj akcje żarówki

1. W projekcie Dodaj odwołanie do *Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll* i ustaw wartość **Kopiuj lokalne** na `False` .

2. Utwórz dwie klasy, imię `UpperCaseSuggestedAction` i drugie o nazwie `LowerCaseSuggestedAction` . Obie klasy implementują <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> .

    ```csharp
    internal class UpperCaseSuggestedAction : ISuggestedAction
    internal class LowerCaseSuggestedAction : ISuggestedAction
    ```

     Obie klasy są podobne, z wyjątkiem tego, że jedno wywołanie <xref:System.String.ToUpper%2A> i inne wywołania <xref:System.String.ToLower%2A> . Poniższe kroki dotyczą tylko klasy akcji wielkich liter, ale należy zaimplementować obie klasy. Wykonaj kroki w celu wdrożenia działania z wielką literą jako wzorca dla wdrożenia akcji małymi literami.

3. Dodaj następujące dyrektywy using dla następujących klas:

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

5. Dodaj konstruktora, który ustawia pola.

    ```csharp
    public UpperCaseSuggestedAction(ITrackingSpan span)
    {
        m_span = span;
        m_snapshot = span.TextBuffer.CurrentSnapshot;
        m_upper = span.GetText(m_snapshot).ToUpper();
        m_display = string.Format("Convert '{0}' to upper case", span.GetText(m_snapshot));
    }
    ```

6. Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A> metodę, aby wyświetlić podgląd akcji.

    ```csharp
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)
    {
        var textBlock = new TextBlock();
        textBlock.Padding = new Thickness(5);
        textBlock.Inlines.Add(new Run() { Text = m_upper });
        return Task.FromResult<object>(textBlock);
    }
    ```

7. Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A> metodę, tak aby zwracała puste <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> Wyliczenie.

    ```csharp
    public Task<IEnumerable<SuggestedActionSet>> GetActionSetsAsync(CancellationToken cancellationToken)
    {
        return Task.FromResult<IEnumerable<SuggestedActionSet>>(null);
    }
    ```

8. Zaimplementuj właściwości w następujący sposób.

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

9. Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A> metodę, zamieniając tekst w zakresie na jego wielką literę.

    ```csharp
    public void Invoke(CancellationToken cancellationToken)
    {
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);
    }
    ```

    > [!WARNING]
    > Metoda **Invoke** działania żarówki nie powinna wyświetlać interfejsu użytkownika. Jeśli akcja zostanie wyświetlona przy użyciu nowego interfejsu użytkownika (na przykład okna dialogowego podglądu lub wyboru), nie wyświetlaj interfejsu użytkownika bezpośrednio z poziomu metody **Invoke** , ale zamiast tego Zaplanuj, aby wyświetlić interfejs użytkownika po powrocie z **wywołania**.

10. Aby ukończyć implementację, Dodaj `Dispose()` metody i `TryGetTelemetryId()` .

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

11. Nie zapomnij pamiętać o `LowerCaseSuggestedAction` zmianie wyświetlanego tekstu na "Konwertuj" {0} na małe litery "i wywołaniu metody <xref:System.String.ToUpper%2A> <xref:System.String.ToLower%2A> .

## <a name="build-and-test-the-code"></a>Kompiluj i Testuj kod
 Aby przetestować ten kod, skompiluj rozwiązanie LightBulbTest i uruchom je w eksperymentalnym wystąpieniu.

1. Skompiluj rozwiązanie.

2. Po uruchomieniu tego projektu w debugerze uruchomione jest drugie wystąpienie programu Visual Studio.

3. Utwórz plik tekstowy i wpisz tekst. Powinna zostać wyświetlona żarówka z lewej strony tekstu.

     ![Testowanie żarówki](../extensibility/media/testlightbulb.png "TestLIghtBulb")

4. Wskaż żarówkę. Powinna zostać wyświetlona strzałka w dół.

5. Po kliknięciu żarówki należy wyświetlić dwie sugerowane akcje, wraz z podglądem wybranej akcji.

     ![Lampa światła testowego, rozwinięta](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")

6. Po kliknięciu pierwszej akcji cały tekst w bieżącym wyrazie powinien zostać przekonwertowany na wielkie litery. Po kliknięciu drugiej akcji wszystkie teksty powinny być konwertowane na małe litery.
