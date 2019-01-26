---
title: 'Przewodnik: Wyróżnianie tekstu | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - highlight text
ms.assetid: 64b772ad-4392-42e9-a237-5137f0384bf0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 272c460b4ee0f171548c29793470b7fccfab601b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54945254"
---
# <a name="walkthrough-highlight-text"></a>Przewodnik: Wyróżnianie tekstu
Możesz dodać różne efekty do edytora, tworząc części składowe Managed Extensibility Framework (MEF). W tym instruktażu przedstawiono sposób zaznacz każde wystąpienie bieżącego słowa w pliku tekstowym. Jeśli słowa występuje więcej niż jeden raz w pliku tekstowym, a następnie pozycji karetki w jedno wystąpienie, każde wystąpienie jest wyróżniona.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, nie instaluj programu Visual Studio SDK z Centrum pobierania. Został on uwzględniony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalacji programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-mef-project"></a>Utwórz projekt MEF  
  
1.  Utwórz projekt VSIX języka C#. (W **nowy projekt** okno dialogowe, wybierz opcję **Visual C# / rozszerzalności**, następnie **projekt VSIX**.) Nazwij rozwiązanie `HighlightWordTest`.  
  
2.  Dodaj szablon elementu edytora klasyfikatora do projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Usuń istniejące pliki klasy.  
  
## <a name="define-a-textmarkertag"></a>Zdefiniuj TextMarkerTag  
 Pierwszym krokiem podczas wyróżniania tekstu jest podklasą <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> i zdefiniować wygląd.  
  
### <a name="to-define-a-textmarkertag-and-a-markerformatdefinition"></a>Aby zdefiniować TextMarkerTag i MarkerFormatDefinition  
  
1.  Dodaj plik klasy i nadaj mu nazwę **HighlightWordTag**.  
  
2.  Dodaj następujące odwołania:  
  
    1.  Microsoft.VisualStudio.CoreUtility  
  
    2.  Microsoft.VisualStudio.Text.Data  
  
    3.  Microsoft.VisualStudio.Text.Logic  
  
    4.  Microsoft.VisualStudio.Text.UI  
  
    5.  Microsoft.VisualStudio.Text.UI.Wpf  
  
    6.  System.ComponentModel.Composition  
  
    7.  Presentation.Core  
  
    8.  Presentation.Framework  
  
3.  Zaimportuj następujące przestrzenie nazw.  
  
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
  
4.  Utwórz klasę, która dziedziczy z <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> i nadaj mu nazwę `HighlightWordTag`.  
  
    ```csharp  
    internal class HighlightWordTag : TextMarkerTag  
    {  
  
    }  
    ```  
  
5.  Tworzenie drugiej klasy, która dziedziczy <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>i nadaj mu nazwę `HighlightWordFormatDefinition`. Aby użyć tej definicji formatu dla tag, należy go wyeksportować z następującymi atrybutami:  
  
    -   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: tagów umożliwia odwoływać się do tego formatu  
  
    -   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: powoduje to, że format są wyświetlane w interfejsie użytkownika  
  
    ```csharp  
  
    [Export(typeof(EditorFormatDefinition))]  
    [Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]  
    [UserVisible(true)]  
    internal class HighlightWordFormatDefinition : MarkerFormatDefinition  
    {  
  
    }  
    ```  
  
6.  W Konstruktorze HighlightWordFormatDefinition określ jej nazwę wyświetlaną i wygląd. Właściwość tło Określa kolor wypełnienia podczas, gdy właściwość pierwszego planu definiuje kolor obramowania.  
  
    ```csharp  
    public HighlightWordFormatDefinition()  
    {  
                this.BackgroundColor = Colors.LightBlue;  
        this.ForegroundColor = Colors.DarkBlue;  
        this.DisplayName = "Highlight Word";  
        this.ZOrder = 5;  
    }  
    ```  
  
7.  W Konstruktorze HighlightWordTag należy przekazać nazwę definicji formatu, utworzony.  
  
    ```  
    public HighlightWordTag() : base("MarkerFormatDefinition/HighlightWordFormatDefinition") { }  
    ```  
  
## <a name="implement-an-itagger"></a>Implementowanie ITagger  
 Następnym krokiem jest zaimplementowanie <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> interfejsu. Ten interfejs przypisuje do bufora podanego tekstu, tagów, które zapewniają wyróżnianie tekstu i innych efektów wizualnych.  
  
### <a name="to-implement-a-tagger"></a>Aby zaimplementować moduł tagujący  
  
1.  Utwórz klasę, która implementuje <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> typu `HighlightWordTag`i nadaj mu nazwę `HighlightWordTagger`.  
  
    ```csharp  
    internal class HighlightWordTagger : ITagger<HighlightWordTag>  
    {  
  
    }  
    ```  
  
2.  Dodaj następujące pola prywatne i właściwości do klasy:  
  
    -   <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, Która odnosi się do bieżącego widoku tekstu.  
  
    -   <xref:Microsoft.VisualStudio.Text.ITextBuffer>, Która odnosi się do buforu tekstowego, która jest podporządkowana narzędziu widoku tekstu.  
  
    -   <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>, Która jest używana do znajdowania tekstu.  
  
    -   <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, Który posiada metody poruszanie się w obrębie zakresy tekstu.  
  
    -   Element <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>, który zawiera zbiór słów, aby wyróżnić.  
  
    -   A <xref:Microsoft.VisualStudio.Text.SnapshotSpan>, która odnosi się do bieżącego słowa.  
  
    -   A <xref:Microsoft.VisualStudio.Text.SnapshotPoint>, która odnosi się do bieżącego położenia karetki.  
  
    -   Obiekt blokady.  
  
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
  
3.  Dodaj Konstruktor, który inicjuje właściwości wymienione wcześniej oraz dodaje <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> i <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> procedury obsługi zdarzeń.  
  
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
  
4.  Programy obsługi zdarzeń, oba wywołania `UpdateAtCaretPosition` metody.  
  
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
  
5.  Musisz również dodać `TagsChanged` zdarzeń, która jest wywoływana przez metodę aktualizacji.  
  
     [!code-csharp[VSSDKHighlightWordTest#10](../extensibility/codesnippet/CSharp/walkthrough-highlighting-text_1.cs)]
     [!code-vb[VSSDKHighlightWordTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-highlighting-text_1.vb)]  
  
6.  `UpdateAtCaretPosition()` Metoda znajdzie każdy wyraz w buforze tekstu, która jest taka sama jak word, gdy kursor znajduje i tworzy listę <xref:Microsoft.VisualStudio.Text.SnapshotSpan> obiektów, które odpowiadają wystąpienia wyrazu. Następnie wywołuje `SynchronousUpdate`, co powoduje zdarzenie `TagsChanged` zdarzeń.  
  
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
  
7.  `SynchronousUpdate` Wykonuje synchroniczne aktualizacji na `WordSpans` i `CurrentWord` właściwości i wywołuje `TagsChanged` zdarzeń.  
  
    ```vb  
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
  
8.  Musisz zaimplementować <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metody. Ta metoda przyjmuje zbiór <xref:Microsoft.VisualStudio.Text.SnapshotSpan> obiekty i zwraca wyliczenie zakresy znaczników.  
  
     W języku C# należy zaimplementować tę metodę jako iterator "yield" umożliwia obliczanie z opóźnieniem (czyli Szacowanie zestaw tylko wtedy, gdy poszczególne elementy są dostępne) tagów. W języku Visual Basic Dodawanie tagów do listy i zwrócić listę.  
  
     W tym miejscu metoda zwraca <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> obiekt, który ma "niebieski" <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>, zapewniającą niebieskim tłem.  
  
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
  
## <a name="create-a-tagger-provider"></a>Tworzenie dostawcy moduł Tagujący  
 Aby utworzyć swoje moduł tagujący, należy zaimplementować <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>. Ta klasa jest część MEF, musisz więc ustawić prawidłowe atrybuty tak, aby to rozszerzenie jest rozpoznawane.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat MEF, zobacz [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).  
  
### <a name="to-create-a-tagger-provider"></a>Aby utworzyć dostawcę moduł tagujący  
  
1.  Utwórz klasę o nazwie `HighlightWordTaggerProvider` implementującej <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>i wyeksportuj go z <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> z "text" i <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> z <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
    ```csharp  
    [Export(typeof(IViewTaggerProvider))]  
    [ContentType("text")]  
    [TagType(typeof(TextMarkerTag))]  
    internal class HighlightWordTaggerProvider : IViewTaggerProvider  
    { }  
    ```  
  
2.  Należy zaimportować dwóch usług edytora i <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService> i <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, aby utworzyć wystąpienie moduł tagujący.  
  
    ```csharp  
    [Import]  
    internal ITextSearchService TextSearchService { get; set; }  
  
    [Import]  
    internal ITextStructureNavigatorSelectorService TextStructureNavigatorSelector { get; set; }  
  
    ```  
  
3.  Implementowanie <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> metodę, aby zwrócić wystąpienia `HighlightWordTagger`.  
  
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
 Aby przetestować ten kod, Kompiluj rozwiązanie HighlightWordTest, a następnie uruchomić go w doświadczalnym wystąpieniu.  
  
### <a name="to-build-and-test-the-highlightwordtest-solution"></a>Aby skompilować i przetestować rozwiązanie HighlightWordTest  
  
1.  Skompiluj rozwiązanie.  
  
2.  Po uruchomieniu tego projektu w debugerze, drugie wystąpienie programu Visual Studio został uruchomiony.  
  
3.  Utwórz plik tekstowy, a następnie wpisz dowolny tekst, w których wyrazy są powtarzane, na przykład "Witaj hello hello".  
  
4.  Umieść kursor w jednym z wystąpień "hello". Każde wystąpienie powinien być wyróżniony kolorem niebieskim.  
  
## <a name="see-also"></a>Zobacz także  
 [Przewodnik: Połączyć typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)