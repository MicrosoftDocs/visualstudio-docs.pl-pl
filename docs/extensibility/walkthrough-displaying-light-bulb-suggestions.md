---
title: 'Przewodnik: Wyświetlanie sugestii żarówki | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09773e2be81ce51971709db590a07ca9960104fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697473"
---
# <a name="walkthrough-display-light-bulb-suggestions"></a>Instruktaż: Wyświetlanie sugestii żarówki
Żarówki są ikony w edytorze programu Visual Studio, które rozwijają się, aby wyświetlić zestaw akcji, na przykład poprawki problemów zidentyfikowanych przez wbudowane analizatory kodu lub refaktoryzacji kodu.

 W edytorach Visual C# i Visual Basic można również użyć platformy kompilatora platformy .NET ("Roslyn"), aby napisać i spakować własne analizatory kodu z akcjami, które automatycznie wyświetlają żarówki. Aby uzyskać więcej informacji, zobacz:

- [Jak: Napisz diagnostykę języka C# i poprawkę kodu](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)

- [Jak: Napisz diagnostykę języka Visual Basic i poprawkę kodu](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)

  Inne języki, takie jak C++ również zapewnić żarówki dla niektórych szybkich akcji, takich jak sugestia, aby utworzyć implementację skrótu tej funkcji.

  Oto jak wygląda żarówka. W projekcie Visual Basic lub Visual C# czerwony squiggle pojawia się pod nazwą zmiennej, gdy jest nieprawidłowa. Jeśli najedziesz myszką na nieprawidłowy identyfikator, żarówka pojawi się w pobliżu kursora.

  ![Żarówki](../extensibility/media/lightbulb.png "Żarówka")

  Jeśli klikniesz strzałkę w dół przez żarówkę, pojawi się zestaw sugerowanych akcji wraz z podglądem wybranej akcji. W takim przypadku pokazuje zmiany, które są wprowadzane do kodu, jeśli wykonać akcję.

  ![podgląd żarówki](../extensibility/media/lightbulbpreview.png "LightBulbPreview")

  Możesz użyć żarówek, aby zapewnić własne sugerowane działania. Na przykład można udostępnić akcje, aby przenieść otwierające nawiasy klamrowe do nowej linii lub przenieść je na koniec poprzedniego wiersza. W poniższym przewodniku pokazano, jak utworzyć żarówkę, która pojawia się w bieżącym słowie i ma dwie sugerowane akcje: **Konwertuj na wielkie litery** i **Konwertuj na małe litery**.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować visual studio SDK z centrum pobierania. Jest on dołączony jako opcjonalna funkcja w konfiguracji programu Visual Studio. Można również zainstalować vs SDK później. Aby uzyskać więcej informacji, zobacz [Instalowanie pakietu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Tworzenie projektu managed extensibility Framework (MEF)

1. Utwórz projekt VSIX języka C#. (W oknie dialogowym **Nowy projekt** wybierz pozycję **Visual C# / Extensibility**, a następnie **VSIX Project**.) Nazwij `LightBulbTest`rozwiązanie .

2. Dodaj szablon elementu **klasyfikatora edytora** do projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia z szablonem elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Usuń istniejące pliki klas.

4. Dodaj następujące odwołanie do projektu i ustaw `False` **polecenie Kopiuj lokalnie** na:

     *Microsoft.VisualStudio.Language.Intellisense*

5. Dodaj nowy plik klasy i nazwij go **LightBulbTest**.

6. Dodaj następujące za pomocą dyrektyw:

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

## <a name="implement-the-light-bulb-source-provider"></a>Wdrożenie dostawcy źródła żarówki

1. W pliku klasy *LightBulbTest.cs* usuń Klasę LightBulbTest. Dodaj klasę o nazwie **TestSuggestedActionsSourceProvider,** która implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>. Wyeksportuj go z nazwą <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> **testu sugerowane akcje** i "tekst".

    ```csharp
    [Export(typeof(ISuggestedActionsSourceProvider))]
    [Name("Test Suggested Actions")]
    [ContentType("text")]
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider
    ```

2. Wewnątrz klasy dostawcy źródłowego <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> zaimportuj i dodaj ją jako właściwość.

    ```csharp
    [Import(typeof(ITextStructureNavigatorSelectorService))]
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }
    ```

3. <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> metodę zwracania obiektu. Źródło jest omówione w następnej sekcji.

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

## <a name="implement-the-isuggestedactionsource"></a>Implementowanie źródła ISuggestedActionSource
 Sugerowane źródło akcji jest odpowiedzialne za zbieranie zestawu sugerowanych akcji i dodawanie ich w odpowiednim kontekście. W takim przypadku kontekst jest bieżącym słowem, a sugerowane akcje to **Wielkie literySuggestedAction** i **LowerCaseSuggestedAction**, które zostały omówione w poniższej sekcji.

1. Dodaj klasę **TestSuggestedActionsSource,** <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>która implementuje .

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

4. Dodaj metodę prywatną, która zwraca wyraz, który jest obecnie pod kursorem. Poniższa metoda analizuje bieżącą lokalizację kursora i pyta nawigatora struktury tekstu o zakres wyrazu. Jeśli kursor znajduje się na <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> słowie, jest zwracany w out parametr; w przeciwnym `out` razie `null` parametr jest `false`i metoda zwraca .

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

5. Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A> metodę. Edytor wywołuje tę metodę, aby dowiedzieć się, czy wyświetlić żarówkę. To wywołanie jest często, na przykład, gdy kursor przechodzi z jednej linii do drugiej lub gdy mysz najeżdża kursor na błąd squiggle. Jest asynchroniczne, aby umożliwić inne operacje interfejsu użytkownika do kontynuowania, gdy ta metoda działa. W większości przypadków ta metoda musi wykonać pewne analizowanie i analizę bieżącego wiersza, więc przetwarzanie może zająć trochę czasu.

     W tej implementacji asynchronicznie <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> pobiera i określa, czy zakres jest znaczący, jak w, czy ma jakiś tekst inny niż odstępy.

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

6. Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> metodę, <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> która zwraca <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> tablicę obiektów, które zawierają różne obiekty. Ta metoda jest wywoływana, gdy żarówka jest rozszerzana.

    > [!WARNING]
    > Należy upewnić się, że `HasSuggestedActionsAsync()` `GetSuggestedActions()` implementacje i są spójne; oznacza to, `HasSuggestedActionsAsync()` `true`że `GetSuggestedActions()` jeśli zwraca , a następnie powinny mieć pewne akcje do wyświetlenia. W wielu `HasSuggestedActionsAsync()` przypadkach, nazywa `GetSuggestedActions()`się tuż przed , ale nie zawsze tak jest. Na przykład, jeśli użytkownik wywołuje akcje żarówki przez naciśnięcie `GetSuggestedActions()` **(CTRL +** .) jest wywoływana tylko.

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

8. Aby zakończyć implementację, dodaj `Dispose()` `TryGetTelemetryId()` implementacje dla i metod. Nie chcesz robić telemetrii, więc `false` po prostu wróć `Empty`i ustaw identyfikator GUID na .

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

## <a name="implement-light-bulb-actions"></a>Wdrażanie działań żarówek

1. W projekcie dodaj odwołanie do pliku *Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll* `False`i ustaw **polecenie Kopiuj lokalnie** na .

2. Utwórz dwie klasy, `UpperCaseSuggestedAction` pierwszą `LowerCaseSuggestedAction`o nazwie i drugą o nazwie . Obie klasy <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>implementują .

    ```csharp
    internal class UpperCaseSuggestedAction : ISuggestedAction
    internal class LowerCaseSuggestedAction : ISuggestedAction
    ```

     Obie klasy są podobne, <xref:System.String.ToUpper%2A> z tą <xref:System.String.ToLower%2A>różnicą, że jedno wywołuje, a inne wywołuje . Poniższe kroki obejmują tylko wielką klasę akcji, ale należy zaimplementować obie klasy. Użyj kroków implementowania akcji wielkich liter jako wzorca do implementowania akcji małych liter.

3. Dodaj następujące przy użyciu dyrektyw dla tych klas:

    ```csharp
    using Microsoft.VisualStudio.Imaging.Interop;
    using System.Windows;
    using System.Windows.Controls;
    using System.Windows.Documents;
    using System.Windows.Media;

    ```

4. Deklaruj zestaw pól prywatnych.

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

6. Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A> metodę tak, aby wyświetlała podgląd akcji.

    ```csharp
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)
    {
        var textBlock = new TextBlock();
        textBlock.Padding = new Thickness(5);
        textBlock.Inlines.Add(new Run() { Text = m_upper });
        return Task.FromResult<object>(textBlock);
    }
    ```

7. Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A> metodę, <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> tak aby zwracała puste wyliczenie.

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

9. Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A> metodę, zastępując tekst w zakresie jego odpowiednikiem wielkich liter.

    ```csharp
    public void Invoke(CancellationToken cancellationToken)
    {
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);
    }
    ```

    > [!WARNING]
    > Akcja żarówki **Invoke** metoda nie oczekuje się pokazać interfejsu użytkownika. Jeśli akcja wywołuje nowy interfejs użytkownika (na przykład okno dialogowe podglądu lub zaznaczania), nie wyświetlaj interfejsu użytkownika bezpośrednio z poziomu metody **Invoke,** ale zamiast tego planuje wyświetlać interfejs użytkownika po powrocie z **invoke**.

10. Aby zakończyć implementację, dodaj `Dispose()` metody i. `TryGetTelemetryId()`

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

11. Nie zapomnij zrobić tego samego `LowerCaseSuggestedAction` dla zmiany wyświetlanego tekstu{0}na "Convert ' <xref:System.String.ToUpper%2A> ' <xref:System.String.ToLower%2A>na małe litery" i połączenia do .

## <a name="build-and-test-the-code"></a>Tworzenie i testowanie kodu
 Aby przetestować ten kod, skompiluj rozwiązanie LightBulbTest i uruchom go w wystąpieniu eksperymentalnym.

1. Skompiluj rozwiązanie.

2. Po uruchomieniu tego projektu w debugerze zostanie uruchomione drugie wystąpienie programu Visual Studio.

3. Utwórz plik tekstowy i wpisz tekst. Po lewej stronie tekstu powinna być widoczna żarówka.

     ![przetestować żarówkę](../extensibility/media/testlightbulb.png "TestLIghtBulb (TestLIghtBulb)")

4. Wskaż żarówkę. Powinna zostać wyświetlona strzałka w dół.

5. Po kliknięciu żarówki powinny być wyświetlane dwie sugerowane akcje wraz z podglądem wybranej akcji.

     ![badana żarówka, rozszerzona](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbRozwiń")

6. Jeśli klikniesz pierwszą akcję, cały tekst w bieżącym słowie powinien zostać przekonwertowany na wielkie litery. Jeśli klikniesz drugą akcję, cały tekst powinien zostać przekonwertowany na małe litery.
