---
title: 'Przewodnik: wyróżnianie tekstu | Microsoft Docs'
description: Dowiedz się, jak wyróżnić każde wystąpienie bieżącego wyrazu w pliku tekstowym, dodając efekty wizualne do edytora w tym instruktażu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - highlight text
ms.assetid: 64b772ad-4392-42e9-a237-5137f0384bf0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f9e69f635b18d4ed67b78751ac6179cad04f002c
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217531"
---
# <a name="walkthrough-highlight-text"></a>Wskazówki: wyróżnianie tekstu
Do edytora można dodawać różne efekty wizualne przez tworzenie części składników Managed Extensibility Framework (MEF). W tym instruktażu pokazano, jak wyróżnić każde wystąpienie bieżącego wyrazu w pliku tekstowym. Jeśli słowo występuje więcej niż jeden raz w pliku tekstowym i położenie karetki w jednym wystąpieniu, każde wystąpienie zostanie wyróżnione.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dołączana jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Tworzenie projektu MEF

1. Utwórz projekt VSIX języka C#. (W oknie dialogowym **Nowy projekt** wybierz pozycję **Visual C#/rozszerzalność**, a następnie **Projekt VSIX**). Nadaj nazwę rozwiązanie `HighlightWordTest` .

2. Dodaj szablon elementu klasyfikatora edytora do projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Usuń istniejące pliki klas.

## <a name="define-a-textmarkertag"></a>Zdefiniuj TextMarkerTag
 Pierwszym krokiem w wyróżnieniu tekstu jest podklasa <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> i Definiowanie jego wyglądu.

### <a name="to-define-a-textmarkertag-and-a-markerformatdefinition"></a>Aby zdefiniować TextMarkerTag i MarkerFormatDefinition

1. Dodaj plik klasy i nadaj mu nazwę **HighlightWordTag**.

2. Dodaj następujące odwołania:

    1. Microsoft. VisualStudio. CoreUtility

    2. Microsoft. VisualStudio. Text. Data

    3. Microsoft. VisualStudio. Text. Logic

    4. Microsoft. VisualStudio. Text. UI

    5. Microsoft. VisualStudio. Text. UI. WPF

    6. System. ComponentModel. kompozycji

    7. Prezentacja. Core

    8. Prezentacja. Struktura

3. Zaimportuj następujące przestrzenie nazw.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Composition;
    using System.Linq;
    using System.Threading;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Classification;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Text.Operations;
    using Microsoft.VisualStudio.Text.Tagging;
    using Microsoft.VisualStudio.Utilities;
    using System.Windows.Media;
    ```

4. Utwórz klasę, która dziedziczy po <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> i nadaj jej nazwę `HighlightWordTag` .

    ```csharp
    internal class HighlightWordTag : TextMarkerTag
    {

    }
    ```

5. Utwórz drugą klasę, która dziedziczy po <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> , i nadaj jej nazwę `HighlightWordFormatDefinition` . Aby można było użyć tej definicji formatu dla tagu, należy wyeksportować go z następującymi atrybutami:

    - <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: Tagi służą do odwoływania się do tego formatu

    - <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: powoduje, że format pojawia się w interfejsie użytkownika

    ```csharp

    [Export(typeof(EditorFormatDefinition))]
    [Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]
    [UserVisible(true)]
    internal class HighlightWordFormatDefinition : MarkerFormatDefinition
    {

    }
    ```

6. W konstruktorze dla HighlightWordFormatDefinition Zdefiniuj jego nazwę wyświetlaną i wygląd. Właściwość Background definiuje kolor wypełnienia, natomiast Właściwość pierwszego planu definiuje kolor obramowania.

    ```csharp
    public HighlightWordFormatDefinition()
    {
        this.BackgroundColor = Colors.LightBlue;
        this.ForegroundColor = Colors.DarkBlue;
        this.DisplayName = "Highlight Word";
        this.ZOrder = 5;
    }
    ```

7. W konstruktorze dla HighlightWordTag, przekaż nazwę utworzonej definicji formatu.

    ```
    public HighlightWordTag() : base("MarkerFormatDefinition/HighlightWordFormatDefinition") { }
    ```

## <a name="implement-an-itagger"></a>Implementowanie elementu ITagger
 Następnym krokiem jest zaimplementowanie <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> interfejsu. Ten interfejs przypisuje do danego buforu tekstowego Tagi, które zapewniają wyróżnianie tekstu i inne efekty wizualne.

### <a name="to-implement-a-tagger"></a>Aby zaimplementować moduł tagujący

1. Utwórz klasę implementującą <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> Typ `HighlightWordTag` i nadaj jej nazwę `HighlightWordTagger` .

    ```csharp
    internal class HighlightWordTagger : ITagger<HighlightWordTag>
    {

    }
    ```

2. Dodaj następujące prywatne pola i właściwości do klasy:

    - Obiekt <xref:Microsoft.VisualStudio.Text.Editor.ITextView> , który odpowiada bieżącemu widokowi tekstu.

    - Obiekt <xref:Microsoft.VisualStudio.Text.ITextBuffer> , który odnosi się do bufora tekstu, który jest zależny od widoku tekstu.

    - Obiekt <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService> , który jest używany do znajdowania tekstu.

    - Element <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> , który ma metody nawigowania w obrębie tekstu.

    - A <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> , który zawiera zestaw wyrazów do wyróżnienia.

    - A <xref:Microsoft.VisualStudio.Text.SnapshotSpan> , który odnosi się do bieżącego wyrazu.

    - A <xref:Microsoft.VisualStudio.Text.SnapshotPoint> , który odnosi się do bieżącej pozycji karetki.

    - Obiekt blokady.

    ```csharp
    ITextView View { get; set; }
    ITextBuffer SourceBuffer { get; set; }
    ITextSearchService TextSearchService { get; set; }
    ITextStructureNavigator TextStructureNavigator { get; set; }
    NormalizedSnapshotSpanCollection WordSpans { get; set; }
    SnapshotSpan? CurrentWord { get; set; }
    SnapshotPoint RequestedPoint { get; set; }
    object updateLock = new object();

    ```

3. Dodaj konstruktora inicjującego wymienione wcześniej właściwości i <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> programy obsługi zdarzeń.

    ```csharp
    public HighlightWordTagger(ITextView view, ITextBuffer sourceBuffer, ITextSearchService textSearchService,
    ITextStructureNavigator textStructureNavigator)
    {
        this.View = view;
        this.SourceBuffer = sourceBuffer;
        this.TextSearchService = textSearchService;
        this.TextStructureNavigator = textStructureNavigator;
        this.WordSpans = new NormalizedSnapshotSpanCollection();
        this.CurrentWord = null;
        this.View.Caret.PositionChanged += CaretPositionChanged;
        this.View.LayoutChanged += ViewLayoutChanged;
    }

    ```

4. Programy obsługi zdarzeń wywołują `UpdateAtCaretPosition` metodę.

    ```csharp
    void ViewLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)
    {
        // If a new snapshot wasn't generated, then skip this layout 
        if (e.NewSnapshot != e.OldSnapshot)
        {
            UpdateAtCaretPosition(View.Caret.Position);
        }
    }

    void CaretPositionChanged(object sender, CaretPositionChangedEventArgs e)
    {
        UpdateAtCaretPosition(e.NewPosition);
    }
    ```

5. Należy również dodać `TagsChanged` zdarzenie, które jest wywoływane przez metodę Update.

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkhighlightwordtest/cs/highlightwordtag.cs" id="Snippet10":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhighlightwordtest/vb/highlightwordtag.vb" id="Snippet10":::


6. `UpdateAtCaretPosition()`Metoda znajduje każdy wyraz w buforze tekstowym, który jest identyczny z słowem, w którym znajduje się kursor i tworzy listę <xref:Microsoft.VisualStudio.Text.SnapshotSpan> obiektów, które odpowiadają wystąpieniu wyrazu. Następnie wywołuje metodę `SynchronousUpdate` , która wywołuje `TagsChanged` zdarzenie.

    ```csharp
    void UpdateAtCaretPosition(CaretPosition caretPosition)
    {
        SnapshotPoint? point = caretPosition.Point.GetPoint(SourceBuffer, caretPosition.Affinity);

        if (!point.HasValue)
            return;

        // If the new caret position is still within the current word (and on the same snapshot), we don't need to check it 
        if (CurrentWord.HasValue
            && CurrentWord.Value.Snapshot == View.TextSnapshot
            && point.Value >= CurrentWord.Value.Start
            && point.Value <= CurrentWord.Value.End)
        {
            return;
        }

        RequestedPoint = point.Value;
        UpdateWordAdornments();
    }

    void UpdateWordAdornments()
    {
        SnapshotPoint currentRequest = RequestedPoint;
        List<SnapshotSpan> wordSpans = new List<SnapshotSpan>();
        //Find all words in the buffer like the one the caret is on
        TextExtent word = TextStructureNavigator.GetExtentOfWord(currentRequest);
        bool foundWord = true;
        //If we've selected something not worth highlighting, we might have missed a "word" by a little bit
        if (!WordExtentIsValid(currentRequest, word))
        {
            //Before we retry, make sure it is worthwhile 
            if (word.Span.Start != currentRequest
                 || currentRequest == currentRequest.GetContainingLine().Start
                 || char.IsWhiteSpace((currentRequest - 1).GetChar()))
            {
                foundWord = false;
            }
            else
            {
                // Try again, one character previous.  
                //If the caret is at the end of a word, pick up the word.
                word = TextStructureNavigator.GetExtentOfWord(currentRequest - 1);

                //If the word still isn't valid, we're done 
                if (!WordExtentIsValid(currentRequest, word))
                    foundWord = false;
            }
        }

        if (!foundWord)
        {
            //If we couldn't find a word, clear out the existing markers
            SynchronousUpdate(currentRequest, new NormalizedSnapshotSpanCollection(), null);
            return;
        }

        SnapshotSpan currentWord = word.Span;
        //If this is the current word, and the caret moved within a word, we're done. 
        if (CurrentWord.HasValue && currentWord == CurrentWord)
            return;

        //Find the new spans
        FindData findData = new FindData(currentWord.GetText(), currentWord.Snapshot);
        findData.FindOptions = FindOptions.WholeWord | FindOptions.MatchCase;

        wordSpans.AddRange(TextSearchService.FindAll(findData));

        //If another change hasn't happened, do a real update 
        if (currentRequest == RequestedPoint)
            SynchronousUpdate(currentRequest, new NormalizedSnapshotSpanCollection(wordSpans), currentWord);
    }
    static bool WordExtentIsValid(SnapshotPoint currentRequest, TextExtent word)
    {
        return word.IsSignificant
            && currentRequest.Snapshot.GetText(word.Span).Any(c => char.IsLetter(c));
    }

    ```

7. `SynchronousUpdate`Wykonuje aktualizację synchroniczną we `WordSpans` `CurrentWord` właściwościach i i wywołuje `TagsChanged` zdarzenie.

    ```csharp
    void SynchronousUpdate(SnapshotPoint currentRequest, NormalizedSnapshotSpanCollection newSpans, SnapshotSpan? newCurrentWord)
    {
        lock (updateLock)
        {
            if (currentRequest != RequestedPoint)
                return;

            WordSpans = newSpans;
            CurrentWord = newCurrentWord;

            var tempEvent = TagsChanged;
            if (tempEvent != null)
                tempEvent(this, new SnapshotSpanEventArgs(new SnapshotSpan(SourceBuffer.CurrentSnapshot, 0, SourceBuffer.CurrentSnapshot.Length)));
        }
    }
    ```

8. Należy zaimplementować <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodę. Ta metoda pobiera kolekcję <xref:Microsoft.VisualStudio.Text.SnapshotSpan> obiektów i zwraca Wyliczenie zakresów znaczników.

     W języku C# Zaimplementuj tę metodę jako iterator, który umożliwia ocenę z opóźnieniem (czyli oszacowanie zestawu tylko w przypadku uzyskiwania dostępu do poszczególnych elementów) tagów. W Visual Basic Dodaj znaczniki do listy i zwróć listę.

     W tym miejscu Metoda zwraca <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> obiekt, który ma wartość "Blue" <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> , która zapewnia niebieskie tło.

    ```csharp
    public IEnumerable<ITagSpan<HighlightWordTag>> GetTags(NormalizedSnapshotSpanCollection spans)
    {
        if (CurrentWord == null)
            yield break;

        // Hold on to a "snapshot" of the word spans and current word, so that we maintain the same
        // collection throughout
        SnapshotSpan currentWord = CurrentWord.Value;
        NormalizedSnapshotSpanCollection wordSpans = WordSpans;

        if (spans.Count == 0 || wordSpans.Count == 0)
            yield break;

        // If the requested snapshot isn't the same as the one our words are on, translate our spans to the expected snapshot 
        if (spans[0].Snapshot != wordSpans[0].Snapshot)
        {
            wordSpans = new NormalizedSnapshotSpanCollection(
                wordSpans.Select(span => span.TranslateTo(spans[0].Snapshot, SpanTrackingMode.EdgeExclusive)));

            currentWord = currentWord.TranslateTo(spans[0].Snapshot, SpanTrackingMode.EdgeExclusive);
        }

        // First, yield back the word the cursor is under (if it overlaps) 
        // Note that we'll yield back the same word again in the wordspans collection; 
        // the duplication here is expected. 
        if (spans.OverlapsWith(new NormalizedSnapshotSpanCollection(currentWord)))
            yield return new TagSpan<HighlightWordTag>(currentWord, new HighlightWordTag());

        // Second, yield all the other words in the file 
        foreach (SnapshotSpan span in NormalizedSnapshotSpanCollection.Overlap(spans, wordSpans))
        {
            yield return new TagSpan<HighlightWordTag>(span, new HighlightWordTag());
        }
    }
    ```

## <a name="create-a-tagger-provider"></a>Tworzenie dostawcy moduł tagujący
 Aby utworzyć moduł tagujący, należy zaimplementować <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> . Ta klasa jest częścią składnika MEF, więc należy ustawić prawidłowe atrybuty, aby rozszerzenie zostało rozpoznane.

> [!NOTE]
> Aby uzyskać więcej informacji na temat MEF, zobacz [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-create-a-tagger-provider"></a>Aby utworzyć dostawcę moduł tagujący

1. Utwórz klasę o nazwie `HighlightWordTaggerProvider` implementującej <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> i wyeksportuj ją z elementem <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text" i <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> z <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .

    ```csharp
    [Export(typeof(IViewTaggerProvider))]
    [ContentType("text")]
    [TagType(typeof(TextMarkerTag))]
    internal class HighlightWordTaggerProvider : IViewTaggerProvider
    { }
    ```

2. Należy zaimportować dwie usługi edytorów, <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService> i <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> , aby utworzyć wystąpienie moduł tagujący.

    ```csharp
    [Import]
    internal ITextSearchService TextSearchService { get; set; }

    [Import]
    internal ITextStructureNavigatorSelectorService TextStructureNavigatorSelector { get; set; }

    ```

3. Zaimplementuj <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> metodę, aby zwrócić wystąpienie elementu `HighlightWordTagger` .

    ```csharp
    public ITagger<T> CreateTagger<T>(ITextView textView, ITextBuffer buffer) where T : ITag
    {
        //provide highlighting only on the top buffer 
        if (textView.TextBuffer != buffer)
            return null;

        ITextStructureNavigator textStructureNavigator =
            TextStructureNavigatorSelector.GetTextStructureNavigator(buffer);

        return new HighlightWordTagger(textView, buffer, TextSearchService, textStructureNavigator) as ITagger<T>;
    }
    ```

## <a name="build-and-test-the-code"></a>Kompiluj i Testuj kod
 Aby przetestować ten kod, skompiluj rozwiązanie HighlightWordTest i uruchom je w eksperymentalnym wystąpieniu.

### <a name="to-build-and-test-the-highlightwordtest-solution"></a>Aby skompilować i przetestować rozwiązanie HighlightWordTest

1. Skompiluj rozwiązanie.

2. Po uruchomieniu tego projektu w debugerze uruchomione jest drugie wystąpienie programu Visual Studio.

3. Utwórz plik tekstowy i wpisz tekst, w którym wyrazy są powtarzane, na przykład "Hello Hello Hello".

4. Umieść kursor w jednym z wystąpień elementu "Hello". Każde wystąpienie powinno być wyróżnione kolorem niebieskim.

## <a name="see-also"></a>Zobacz też
- [Przewodnik: łączenie typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
