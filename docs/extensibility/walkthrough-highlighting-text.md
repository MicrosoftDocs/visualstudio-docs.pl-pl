---
title: 'Przewodnik: Wyróżnianie tekstu | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - highlight text
ms.assetid: 64b772ad-4392-42e9-a237-5137f0384bf0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c35b1a032993a6c183191aafff77d8adeba4a3ef
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697400"
---
# <a name="walkthrough-highlight-text"></a>Instruktaż: Wyróżnianie tekstu
Można dodać różne efekty wizualne do edytora, tworząc części składowe managed extensibility framework (MEF). W tym przewodniku pokazano, jak wyróżnić każde wystąpienie bieżącego wyrazu w pliku tekstowym. Jeśli wyraz występuje więcej niż jeden raz w pliku tekstowym i umieszczasz daszka w jednym wystąpieniu, każde wystąpienie jest wyróżnione.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować visual studio SDK z centrum pobierania. Jest on dołączony jako opcjonalna funkcja w konfiguracji programu Visual Studio. Można również zainstalować vs SDK później. Aby uzyskać więcej informacji, zobacz [Instalowanie pakietu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Tworzenie projektu MEF

1. Utwórz projekt VSIX języka C#. (W oknie dialogowym **Nowy projekt** wybierz pozycję **Visual C# / Extensibility**, a następnie **VSIX Project**.) Nazwij `HighlightWordTest`rozwiązanie .

2. Dodaj szablon elementu klasyfikatora edytora do projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia z szablonem elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Usuń istniejące pliki klas.

## <a name="define-a-textmarkertag"></a>Definiowanie znacznika tekstowego
 Pierwszym krokiem wyróżniania tekstu jest <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> podklasa i zdefiniowanie jego wyglądu.

### <a name="to-define-a-textmarkertag-and-a-markerformatdefinition"></a>Aby zdefiniować znacznik tekstowy i znacznikformatdefinacja

1. Dodaj plik klasy i nadaj jej nazwę **HighlightWordTag**.

2. Dodaj następujące odwołania:

    1. Microsoft.VisualStudio.CoreUtility

    2. Microsoft.VisualStudio.Text.Data

    3. Microsoft.VisualStudio.Text.Logic

    4. Microsoft.VisualStudio.Text.UI

    5. Microsoft.VisualStudio.Text.UI.Wpf

    6. System.componentmodel.composition

    7. Prezentacja.R.

    8. Prezentacja.Framework

3. Zaimportuj następujące obszary nazw.

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

4. Utwórz klasę, która <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> dziedziczy `HighlightWordTag`i nadaj jej nazwę .

    ```csharp
    internal class HighlightWordTag : TextMarkerTag
    {

    }
    ```

5. Utwórz drugą klasę, <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>która dziedziczy po , i nazwij ją `HighlightWordFormatDefinition`. Aby użyć tej definicji formatu dla tagu, należy wyeksportować go z następującymi atrybutami:

    - <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: tagi używają tego do odwoływania się do tego formatu

    - <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: powoduje to, że format pojawia się w interfejsie użytkownika

    ```csharp

    [Export(typeof(EditorFormatDefinition))]
    [Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]
    [UserVisible(true)]
    internal class HighlightWordFormatDefinition : MarkerFormatDefinition
    {

    }
    ```

6. W konstruktorze highlightWordFormatDefinition zdefiniuj jego nazwę wyświetlaną i wygląd. Background Właściwość definiuje kolor wypełnienia, podczas gdy Właściwość Foreground definiuje kolor obramowania.

    ```csharp
    public HighlightWordFormatDefinition()
    {
                this.BackgroundColor = Colors.LightBlue;
        this.ForegroundColor = Colors.DarkBlue;
        this.DisplayName = "Highlight Word";
        this.ZOrder = 5;
    }
    ```

7. W konstruktorze HighlightWordTag przekaż nazwę utworzonej definicji formatu.

    ```
    public HighlightWordTag() : base("MarkerFormatDefinition/HighlightWordFormatDefinition") { }
    ```

## <a name="implement-an-itagger"></a>Implementowanie ITagger
 Następnym krokiem jest <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> zaimplementowanie interfejsu. Ten interfejs przypisuje do danego buforu tekstu znaczniki, które zapewniają wyróżnianie tekstu i inne efekty wizualne.

### <a name="to-implement-a-tagger"></a>Aby zaimplementować znacznik

1. Utwórz klasę, <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> która `HighlightWordTag`implementuje typ `HighlightWordTagger`, i nazwij ją .

    ```csharp
    internal class HighlightWordTagger : ITagger<HighlightWordTag>
    {

    }
    ```

2. Dodaj do klasy następujące pola prywatne i właściwości:

    - An <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, który odpowiada bieżącemu widokowi tekstu.

    - An <xref:Microsoft.VisualStudio.Text.ITextBuffer>, który odpowiada buforowi tekstowemu, który stanowi podstawę widoku tekstu.

    - An <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>, który służy do znajdowania tekstu.

    - An <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, który ma metody nawigacji w obrębie zakresu tekstu.

    - A <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>, który zawiera zestaw słów do podświetlenia.

    - A <xref:Microsoft.VisualStudio.Text.SnapshotSpan>, który odpowiada bieżącemu wyrazowi.

    - A <xref:Microsoft.VisualStudio.Text.SnapshotPoint>, który odpowiada aktualnej pozycji cieszy.

    - Obiekt blokady.

    ```csharp
    ITextView View { get; set; }
    ITextBuffer SourceBuffer { get; set; }
    ITextSearchService TextSearchService { get; set; }
    ITextStructureNavigator TextStructureNavigator { get; set; }
    NormalizedSnapshotSpanCollection WordSpans { get; set; }
    SnapshotSpan? CurrentWord { get; set; }
    SnapshotPoint RequestedPoint { get; set; }
    object updateLock = new object();

    ```

3. Dodaj konstruktora, który inicjuje <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> właściwości <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> wymienione wcześniej i dodaje i obsługi zdarzeń.

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

4. Programy obsługi zdarzeń zarówno `UpdateAtCaretPosition` wywołać metodę.

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

5. Należy również dodać `TagsChanged` zdarzenie, które jest wywoływane przez metodę aktualizacji.

     [!code-csharp[VSSDKHighlightWordTest#10](../extensibility/codesnippet/CSharp/walkthrough-highlighting-text_1.cs)]
     [!code-vb[VSSDKHighlightWordTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-highlighting-text_1.vb)]

6. Metoda `UpdateAtCaretPosition()` znajduje każde słowo w buforze tekstu, który jest identyczny ze słowem, w <xref:Microsoft.VisualStudio.Text.SnapshotSpan> którym kursor jest umieszczony i konstruuje listę obiektów, które odpowiadają wystąpień wyrazu. Następnie wywołuje `SynchronousUpdate`, co `TagsChanged` podnosi zdarzenie.

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
        //If we've selected something not worth highlighting, we might have missed a "word" by a little bit
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
    static bool WordExtentIsValid(SnapshotPoint currentRequest, TextExtent word)
    {
        return word.IsSignificant
            && currentRequest.Snapshot.GetText(word.Span).Any(c => char.IsLetter(c));
    }

    ```

7. Wykonuje `SynchronousUpdate` aktualizację synchroniczową `WordSpans` właściwości `CurrentWord` i i wywołuje `TagsChanged` zdarzenie.

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

8. Należy zaimplementować <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodę. Ta metoda pobiera <xref:Microsoft.VisualStudio.Text.SnapshotSpan> kolekcję obiektów i zwraca wyliczenie zakresów znaczników.

     W języku C#zaimplementuj tę metodę jako iterator wydajności, który umożliwia powolne oceny (czyli oceny zestawu tylko wtedy, gdy poszczególne elementy są dostępne) tagów. W języku Visual Basic dodaj znaczniki do listy i zwróć listę.

     W tym miejscu <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> metoda zwraca obiekt, <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>który ma "niebieski" , który zapewnia niebieskie tło.

    ```csharp
    public IEnumerable<ITagSpan<HighlightWordTag>> GetTags(NormalizedSnapshotSpanCollection spans)
    {
        if (CurrentWord == null)
            yield break;

        // Hold on to a "snapshot" of the word spans and current word, so that we maintain the same
        // collection throughout
        SnapshotSpan currentWord = CurrentWord.Value;
        NormalizedSnapshotSpanCollection wordSpans = WordSpans;

        if (spans.Count == 0 || wordSpans.Count == 0)
            yield break;

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
            yield return new TagSpan<HighlightWordTag>(currentWord, new HighlightWordTag());

        // Second, yield all the other words in the file 
        foreach (SnapshotSpan span in NormalizedSnapshotSpanCollection.Overlap(spans, wordSpans))
        {
            yield return new TagSpan<HighlightWordTag>(span, new HighlightWordTag());
        }
    }
    ```

## <a name="create-a-tagger-provider"></a>Tworzenie dostawcy znaczników
 Aby utworzyć tager, należy <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>zaimplementować plik . Ta klasa jest częścią składnika MEF, dlatego należy ustawić poprawne atrybuty, aby to rozszerzenie zostało rozpoznane.

> [!NOTE]
> Aby uzyskać więcej informacji na temat MEF, zobacz [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-create-a-tagger-provider"></a>Aby utworzyć dostawcę znaczników

1. Utwórz klasę `HighlightWordTaggerProvider` o <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>nazwie, która implementuje , i wyeksportuj ją z <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "tekstem" i a <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> . <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>

    ```csharp
    [Export(typeof(IViewTaggerProvider))]
    [ContentType("text")]
    [TagType(typeof(TextMarkerTag))]
    internal class HighlightWordTaggerProvider : IViewTaggerProvider
    { }
    ```

2. Należy zaimportować dwie <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService> usługi <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>edytora, i , aby utworzyć wystąpienie tager.

    ```csharp
    [Import]
    internal ITextSearchService TextSearchService { get; set; }

    [Import]
    internal ITextStructureNavigatorSelectorService TextStructureNavigatorSelector { get; set; }

    ```

3. Zaimplementuj <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> metodę `HighlightWordTagger`zwracania wystąpienia .

    ```csharp
    public ITagger<T> CreateTagger<T>(ITextView textView, ITextBuffer buffer) where T : ITag
    {
        //provide highlighting only on the top buffer 
        if (textView.TextBuffer != buffer)
            return null;

        ITextStructureNavigator textStructureNavigator =
            TextStructureNavigatorSelector.GetTextStructureNavigator(buffer);

        return new HighlightWordTagger(textView, buffer, TextSearchService, textStructureNavigator) as ITagger<T>;
    }
    ```

## <a name="build-and-test-the-code"></a>Tworzenie i testowanie kodu
 Aby przetestować ten kod, skompiluj rozwiązanie HighlightWordTest i uruchom go w wystąpieniu eksperymentalnym.

### <a name="to-build-and-test-the-highlightwordtest-solution"></a>Aby skompilować i przetestować rozwiązanie HighlightWordTest

1. Skompiluj rozwiązanie.

2. Po uruchomieniu tego projektu w debugerze zostanie uruchomione drugie wystąpienie programu Visual Studio.

3. Utwórz plik tekstowy i wpisz tekst, w którym słowa są powtarzane, na przykład "hello hello hello hello".

4. Umieść kursor w jednym z wystąpień "hello". Każde wystąpienie powinno być podświetlone na niebiesko.

## <a name="see-also"></a>Zobacz też
- [Instruktaż: łączenie typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
