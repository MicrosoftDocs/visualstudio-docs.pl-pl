---
title: 'Przewodnik: Używanie polecenia powłoki z rozszerzeniem edytora | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - add a menu command
ms.assetid: 08526848-a442-4cd4-afa1-b2eac2005adb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 08c3acb26fe6eed1918dd1f9bb9e84b260defa5e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72632488"
---
# <a name="walkthrough-use-a-shell-command-with-an-editor-extension"></a>Przewodnik: Używanie polecenia powłoki z rozszerzeniem edytora
Z pakietu VSPackage można dodać do edytora funkcje, takie jak polecenia menu. W tym instruktażu przedstawiono sposób dodawania definiowania układu do widoku tekstu w edytorze przez wywoływanie polecenia menu.

 W tym instruktażu przedstawiono użycie pakietu VSPackage wraz z częścią składnika Managed Extensibility Framework (MEF). Aby zarejestrować polecenie menu za pomocą powłoki programu Visual Studio, należy użyć pakietu VSPackage. I można użyć polecenia, aby uzyskać dostęp do części składnika MEF.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dołączana jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-menu-command"></a>Tworzenie rozszerzenia za pomocą polecenia menu
 Utwórz element pakietu VSPackage, który umieszcza polecenie menu o nazwie **Dodaj moduł definiowania** układu w menu **Narzędzia** .

1. Utwórz projekt C# VSIX o nazwie `MenuCommandTest` i Dodaj niestandardową nazwę szablonu elementu polecenia **autodefiniowania**. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Zostanie otwarte rozwiązanie o nazwie MenuCommandTest. Plik MenuCommandTestPackage ma kod, który tworzy polecenie menu i umieszcza je w menu **Narzędzia** . W tym momencie polecenie spowoduje wyświetlenie okna komunikatu. W kolejnych krokach pokazano, jak zmienić ten element, aby wyświetlić jego oznaczenie.

3. Otwórz plik *source. Extension. vsixmanifest* w edytorze manifestu VSIX. Karta `Assets` powinna mieć wiersz dla elementu Microsoft. VisualStudio. pakietu VSPackage o nazwie MenuCommandTest.

4. Zapisz i zamknij plik *source. Extension. vsixmanifest* .

## <a name="add-a-mef-extension-to-the-command-extension"></a>Dodaj rozszerzenie MEF do rozszerzenia polecenia

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł rozwiązanie, kliknij polecenie **Dodaj**, a następnie kliknij pozycję **Nowy projekt**. W oknie dialogowym **Dodaj nowy projekt** kliknij pozycję **rozszerzalność** w **obszarze C#Wizualizacja** , a następnie w polu **Projekt VSIX**. Nadaj nazwę projektowi `CommentAdornmentTest`.

2. Ponieważ ten projekt będzie współpracujący z zestawem pakietu VSPackage o silnej nazwie, należy podpisać zestaw. Można ponownie użyć pliku klucza, który został już utworzony dla zestawu pakietu VSPackage.

    1. Otwórz właściwości projektu i wybierz kartę **podpisywanie** .

    2. Wybierz pozycję **podpisz zestaw**.

    3. W obszarze **Wybierz plik klucza o silnej nazwie**wybierz plik *Key. snk* , który został wygenerowany dla zestawu MenuCommandTest.

## <a name="refer-to-the-mef-extension-in-the-vspackage-project"></a>Odwołaj się do rozszerzenia MEF w projekcie pakietu VSPackage
 Ponieważ dodajesz składnik MEF do pakietu VSPackage, należy określić oba rodzaje zasobów w manifeście.

> [!NOTE]
> Aby uzyskać więcej informacji na temat MEF, zobacz [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-refer-to-the-mef-component-in-the-vspackage-project"></a>Aby odwołać się do składnika MEF w projekcie pakietu VSPackage

1. W projekcie MenuCommandTest Otwórz plik *source. Extension. vsixmanifest* w edytorze manifestu VSIX.

2. Na karcie **zasoby** kliknij pozycję **Nowy**.

3. Na liście **Typ** wybierz **Microsoft. VisualStudio. MefComponent**.

4. Z listy **Źródło** wybierz **projekt w bieżącym rozwiązaniu**.

5. Na liście **projekt** wybierz pozycję **CommentAdornmentTest**.

6. Zapisz i zamknij plik *source. Extension. vsixmanifest* .

7. Upewnij się, że projekt MenuCommandTest ma odwołanie do projektu CommentAdornmentTest.

8. W projekcie CommentAdornmentTest Ustaw projekt, aby utworzyć zestaw. W **Eksplorator rozwiązań**wybierz projekt i poszukaj w oknie **Właściwości** właściwości **Kopiuj dane wyjściowe kompilacji do OutputDirectory** i ustaw dla niej **wartość true**.

## <a name="define-a-comment-adornment"></a>Definiowanie definiowania układu komentarzy
 Sam moduł definiowania komentarza składa się z <xref:Microsoft.VisualStudio.Text.ITrackingSpan>, który śledzi zaznaczony tekst, a niektóre ciągi reprezentujące autora i opis tekstu.

#### <a name="to-define-a-comment-adornment"></a>Aby zdefiniować autodefiniowanie komentarza

1. W projekcie CommentAdornmentTest Dodaj nowy plik klasy i nadaj mu nazwę `CommentAdornment`.

2. Dodaj następujące odwołania:

    1. Microsoft. VisualStudio. CoreUtility

    2. Microsoft. VisualStudio. Text. Data

    3. Microsoft. VisualStudio. Text. Logic

    4. Microsoft. VisualStudio. Text. UI

    5. Microsoft. VisualStudio. Text. UI. WPF

    6. System. ComponentModel. kompozycji

    7. 'Presentationcore

    8. Platformie docelowej

    9. 'Windowsbase

3. Dodaj następującą `using` dyrektywę.

    ```csharp
    using Microsoft.VisualStudio.Text;
    ```

4. Plik powinien zawierać klasę o nazwie `CommentAdornment`.

    ```csharp
    internal class CommentAdornment
    ```

5. Dodaj trzy pola do klasy `CommentAdornment` dla <xref:Microsoft.VisualStudio.Text.ITrackingSpan>, autora i opisu.

    ```csharp
    public readonly ITrackingSpan Span;
    public readonly string Author;
    public readonly string Text;
    ```

6. Dodaj Konstruktor inicjujący pola.

    ```csharp
    public CommentAdornment(SnapshotSpan span, string author, string text)
    {
        this.Span = span.Snapshot.CreateTrackingSpan(span, SpanTrackingMode.EdgeExclusive);
        this.Author = author;
        this.Text = text;
    }
    ```

## <a name="create-a-visual-element-for-the-adornment"></a>Utwórz element wizualny dla definiowania układu
 Zdefiniuj element wizualny dla definiowania układu. W tym instruktażu Zdefiniuj kontrolkę, która dziedziczy z klasy Windows Presentation Foundation (WPF) <xref:System.Windows.Controls.Canvas>.

1. Utwórz klasę w projekcie CommentAdornmentTest i nadaj jej nazwę `CommentBlock`.

2. Dodaj następujące dyrektywy `using`.

    ```csharp
    using Microsoft.VisualStudio.Text;
    using System;
    using System.Windows;
    using System.Windows.Controls;
    using System.Windows.Media;
    using System.Windows.Shapes;
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Utilities;
    ```

3. Uczyń klasę `CommentBlock` dziedziczyć z <xref:System.Windows.Controls.Canvas>.

    ```csharp
    internal class CommentBlock : Canvas
    { }
    ```

4. Dodaj pola prywatne, aby zdefiniować wizualne aspekty definiowania układu.

    ```csharp
    private Geometry textGeometry;
    private Grid commentGrid;
    private static Brush brush;
    private static Pen solidPen;
    private static Pen dashPen;
    ```

5. Dodaj konstruktora, który definiuje oznaczenie i dodaje odpowiedni tekst.

    ```csharp
    public CommentBlock(double textRightEdge, double viewRightEdge,
            Geometry newTextGeometry, string author, string body)
    {
        if (brush == null)
        {
            brush = new SolidColorBrush(Color.FromArgb(0x20, 0x00, 0xff, 0x00));
            brush.Freeze();
            Brush penBrush = new SolidColorBrush(Colors.Green);
            penBrush.Freeze();
            solidPen = new Pen(penBrush, 0.5);
            solidPen.Freeze();
            dashPen = new Pen(penBrush, 0.5);
            dashPen.DashStyle = DashStyles.Dash;
            dashPen.Freeze();
        }

        this.textGeometry = newTextGeometry;

        TextBlock tb1 = new TextBlock();
        tb1.Text = author;
        TextBlock tb2 = new TextBlock();
        tb2.Text = body;

        const int MarginWidth = 8;
        this.commentGrid = new Grid();
        this.commentGrid.RowDefinitions.Add(new RowDefinition());
        this.commentGrid.RowDefinitions.Add(new RowDefinition());
        ColumnDefinition cEdge = new ColumnDefinition();
        cEdge.Width = new GridLength(MarginWidth);
        ColumnDefinition cEdge2 = new ColumnDefinition();
        cEdge2.Width = new GridLength(MarginWidth);
        this.commentGrid.ColumnDefinitions.Add(cEdge);
        this.commentGrid.ColumnDefinitions.Add(new ColumnDefinition());
        this.commentGrid.ColumnDefinitions.Add(cEdge2);

        System.Windows.Shapes.Rectangle rect = new System.Windows.Shapes.Rectangle();
        rect.RadiusX = 6;
        rect.RadiusY = 3;
        rect.Fill = brush;
        rect.Stroke = Brushes.Green;

            Size inf = new Size(double.PositiveInfinity, double.PositiveInfinity);
            tb1.Measure(inf);
            tb2.Measure(inf);
            double middleWidth = Math.Max(tb1.DesiredSize.Width, tb2.DesiredSize.Width);
            this.commentGrid.Width = middleWidth + 2 * MarginWidth;

        Grid.SetColumn(rect, 0);
        Grid.SetRow(rect, 0);
        Grid.SetRowSpan(rect, 2);
        Grid.SetColumnSpan(rect, 3);
        Grid.SetRow(tb1, 0);
        Grid.SetColumn(tb1, 1);
        Grid.SetRow(tb2, 1);
        Grid.SetColumn(tb2, 1);
        this.commentGrid.Children.Add(rect);
        this.commentGrid.Children.Add(tb1);
        this.commentGrid.Children.Add(tb2);

        Canvas.SetLeft(this.commentGrid, Math.Max(viewRightEdge - this.commentGrid.Width - 20.0, textRightEdge + 20.0));
        Canvas.SetTop(this.commentGrid, textGeometry.GetRenderBounds(solidPen).Top);

        this.Children.Add(this.commentGrid);
    }
    ```

6. Zaimplementuj również procedurę obsługi zdarzeń <xref:System.Windows.Controls.Panel.OnRender%2A>, która rysuje Rozrysowanie.

    ```csharp
    protected override void OnRender(DrawingContext dc)
    {
        base.OnRender(dc);
        if (this.textGeometry != null)
        {
            dc.DrawGeometry(brush, solidPen, this.textGeometry);
            Rect textBounds = this.textGeometry.GetRenderBounds(solidPen);
            Point p1 = new Point(textBounds.Right, textBounds.Bottom);
            Point p2 = new Point(Math.Max(Canvas.GetLeft(this.commentGrid) - 20.0, p1.X), p1.Y);
            Point p3 = new Point(Math.Max(Canvas.GetLeft(this.commentGrid), p1.X), (Canvas.GetTop(this.commentGrid) + p1.Y) * 0.5);
            dc.DrawLine(dashPen, p1, p2);
            dc.DrawLine(dashPen, p2, p3);
        }
    }
    ```

## <a name="add-an-iwpftextviewcreationlistener"></a>Dodawanie elementu IWpfTextViewCreationListener
 @No__t_0 jest częścią składnika MEF, która służy do nasłuchiwania zdarzeń tworzenia.

1. Dodaj plik klasy do projektu CommentAdornmentTest i nadaj mu nazwę `Connector`.

2. Dodaj następujące dyrektywy `using`.

    ```csharp
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Utilities;
    ```

3. Zadeklaruj klasę implementującą <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> i wyeksportuj ją z <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text" i <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document>. Atrybut typu zawartości określa rodzaj zawartości, do której stosuje się składnik. Typ tekstu jest typem podstawowym dla wszystkich typów plików Niebinarnych. W związku z tym niemal każdy utworzony widok tekstowy będzie miał ten typ. Atrybut roli widok tekstu określa rodzaj widoku tekstu, do którego ma zastosowanie składnik. Role widoku tekstu dokumentu zwykle pokazują tekst składający się z wierszy i są przechowywane w pliku.

     [!code-vb[VSSDKMenuCommandTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_1.vb)]
     [!code-csharp[VSSDKMenuCommandTest#11](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_1.cs)]

4. Zaimplementuj metodę <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>, tak aby wywołuje zdarzenie static `Create()` `CommentAdornmentManager`.

    ```csharp
    public void TextViewCreated(IWpfTextView textView)
    {
        CommentAdornmentManager.Create(textView);
    }
    ```

5. Dodaj metodę, której można użyć do wykonania polecenia.

    ```csharp
    static public void Execute(IWpfTextViewHost host)
    {
        IWpfTextView view = host.TextView;
        //Add a comment on the selected text. 
        if (!view.Selection.IsEmpty)
        {
            //Get the provider for the comment adornments in the property bag of the view.
            CommentAdornmentProvider provider = view.Properties.GetProperty<CommentAdornmentProvider>(typeof(CommentAdornmentProvider));

            //Add some arbitrary author and comment text. 
            string author = System.Security.Principal.WindowsIdentity.GetCurrent().Name;
            string comment = "Four score....";

            //Add the comment adornment using the provider.
            provider.Add(view.Selection.SelectedSpans[0], author, comment);
        }
    }
    ```

## <a name="define-an-adornment-layer"></a>Definiowanie warstwy definiowania układu
 Aby dodać nowy moduł definiowania układu, należy zdefiniować warstwę definiowania układu.

### <a name="to-define-an-adornment-layer"></a>Aby zdefiniować warstwę definiowania układu

1. W klasie `Connector` Zadeklaruj pole publiczne typu <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition> i wyeksportuj go za pomocą <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, który określa unikatową nazwę warstwy zakończenia i <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>, która definiuje relację z kolejnością z tej warstwy zakończenia do innych warstw widoku tekstu (tekst , karetka i zaznaczenie).

    ```csharp
    [Export(typeof(AdornmentLayerDefinition))]
    [Name("CommentAdornmentLayer")]
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
    public AdornmentLayerDefinition commentLayerDefinition;

    ```

## <a name="provide-comment-adornments"></a>Podaj zakończenia komentarzy
 Po zdefiniowaniu definiowania układu, należy również zaimplementować dostawcę definiowania układu i komentarza. Dostawca autouzupełniania komentarzy zachowuje listę wypełnień komentarzy, nasłuchuje zdarzeń <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> na źródłowym buforze tekstu i usuwa elementy definiowania komentarzy po usunięciu podstawowego tekstu.

1. Dodaj nowy plik klasy do projektu CommentAdornmentTest i nadaj mu nazwę `CommentAdornmentProvider`.

2. Dodaj następujące dyrektywy `using`.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Collections.ObjectModel;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Editor;
    ```

3. Dodaj klasę o nazwie `CommentAdornmentProvider`.

    ```csharp
    internal class CommentAdornmentProvider
    {
    }
    ```

4. Dodaj pola prywatne dla bufora tekstu oraz listę elementów definiowania komentarza związanych z buforem.

    ```csharp
    private ITextBuffer buffer;
    private IList<CommentAdornment> comments = new List<CommentAdornment>();

    ```

5. Dodaj Konstruktor dla `CommentAdornmentProvider`. Ten konstruktor powinien mieć dostęp prywatny, ponieważ dostawca jest skonkretyzowany przez metodę `Create()`. Konstruktor dodaje do zdarzenia <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> obsługę zdarzeń `OnBufferChanged`.

    ```csharp
    private CommentAdornmentProvider(ITextBuffer buffer)
    {
        this.buffer = buffer;
        //listen to the Changed event so we can react to deletions. 
        this.buffer.Changed += OnBufferChanged;
    }

    ```

6. Dodaj metodę `Create()`.

    ```csharp
    public static CommentAdornmentProvider Create(IWpfTextView view)
    {
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentProvider>(delegate { return new CommentAdornmentProvider(view.TextBuffer); });
    }

    ```

7. Dodaj metodę `Detach()`.

    ```csharp
    public void Detach()
    {
        if (this.buffer != null)
        {
            //remove the Changed listener 
            this.buffer.Changed -= OnBufferChanged;
            this.buffer = null;
        }
    }
    ```

8. Dodaj program obsługi zdarzeń `OnBufferChanged`.

     [!code-csharp[VSSDKMenuCommandTest#21](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_2.cs)]
     [!code-vb[VSSDKMenuCommandTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_2.vb)]

9. Dodaj deklarację dla zdarzenia `CommentsChanged`.

    ```csharp
    public event EventHandler<CommentsChangedEventArgs> CommentsChanged;
    ```

10. Utwórz metodę `Add()`, aby dodać moduł definiowania układu.

    ```csharp
    public void Add(SnapshotSpan span, string author, string text)
    {
        if (span.Length == 0)
            throw new ArgumentOutOfRangeException("span");
        if (author == null)
            throw new ArgumentNullException("author");
        if (text == null)
            throw new ArgumentNullException("text");

        //Create a comment adornment given the span, author and text.
        CommentAdornment comment = new CommentAdornment(span, author, text);

        //Add it to the list of comments. 
        this.comments.Add(comment);

        //Raise the changed event.
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;
        if (commentsChanged != null)
            commentsChanged(this, new CommentsChangedEventArgs(comment, null));
    }

    ```

11. Dodaj metodę `RemoveComments()`.

    ```csharp
    public void RemoveComments(SnapshotSpan span)
    {
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;

        //Get a list of all the comments that are being kept
        IList<CommentAdornment> keptComments = new List<CommentAdornment>(this.comments.Count);

        foreach (CommentAdornment comment in this.comments)
        {
            //find out if the given span overlaps with the comment text span. If two spans are adjacent, they do not overlap. To consider adjacent spans, use IntersectsWith. 
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))
            {
                //Raise the change event to delete this comment. 
                if (commentsChanged != null)
                    commentsChanged(this, new CommentsChangedEventArgs(null, comment));
            }
            else
                keptComments.Add(comment);
        }

        this.comments = keptComments;
    }
    ```

12. Dodaj metodę `GetComments()`, która zwraca wszystkie komentarze w danym przedziale.

    ```csharp
    public Collection<CommentAdornment> GetComments(SnapshotSpan span)
    {
        IList<CommentAdornment> overlappingComments = new List<CommentAdornment>();
        foreach (CommentAdornment comment in this.comments)
        {
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))
                overlappingComments.Add(comment);
        }

        return new Collection<CommentAdornment>(overlappingComments);
    }
    ```

13. Dodaj klasę o nazwie `CommentsChangedEventArgs` w następujący sposób.

    ```csharp
    internal class CommentsChangedEventArgs : EventArgs
    {
        public readonly CommentAdornment CommentAdded;

        public readonly CommentAdornment CommentRemoved;

        public CommentsChangedEventArgs(CommentAdornment added, CommentAdornment removed)
        {
            this.CommentAdded = added;
            this.CommentRemoved = removed;
        }
    }
    ```

## <a name="manage-comment-adornments"></a>Zarządzaj autodefiniowaniami komentarzy
 Menedżer definiowania układu komentarzy tworzy oznaczenie i dodaje je do warstwy definiowania układu. Nasłuchuje <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> i <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> zdarzeń, aby można było przenieść lub usunąć moduł definiowania układu. Nasłuchuje również zdarzenia `CommentsChanged`, które jest wywoływane przez dostawcę definiowania monitów, gdy Komentarze są dodawane lub usuwane.

1. Dodaj plik klasy do projektu CommentAdornmentTest i nadaj mu nazwę `CommentAdornmentManager`.

2. Dodaj następujące dyrektywy `using`.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Windows.Media;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Text.Formatting;
    ```

3. Dodaj klasę o nazwie `CommentAdornmentManager`.

    ```csharp
    internal class CommentAdornmentManager
        {
        }
    ```

4. Dodaj niektóre pola prywatne.

    ```csharp
    private readonly IWpfTextView view;
    private readonly IAdornmentLayer layer;
    private readonly CommentAdornmentProvider provider;
    ```

5. Dodaj Konstruktor, który subskrybuje Menedżera do zdarzeń <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> i <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed>, a także zdarzenia `CommentsChanged`. Konstruktor jest prywatny, ponieważ Menedżer tworzy wystąpienie przez metodę static `Create()`.

    ```csharp
    private CommentAdornmentManager(IWpfTextView view)
    {
        this.view = view;
        this.view.LayoutChanged += OnLayoutChanged;
        this.view.Closed += OnClosed;

        this.layer = view.GetAdornmentLayer("CommentAdornmentLayer");

        this.provider = CommentAdornmentProvider.Create(view);
        this.provider.CommentsChanged += OnCommentsChanged;
    }
    ```

6. Dodaj metodę `Create()`, która pobiera dostawcę lub tworzy jeden w razie potrzeby.

    ```csharp
    public static CommentAdornmentManager Create(IWpfTextView view)
    {
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentManager>(delegate { return new CommentAdornmentManager(view); });
    }
    ```

7. Dodaj procedurę obsługi `CommentsChanged`.

    ```csharp
    private void OnCommentsChanged(object sender, CommentsChangedEventArgs e)
    {
        //Remove the comment (when the adornment was added, the comment adornment was used as the tag). 
        if (e.CommentRemoved != null)
            this.layer.RemoveAdornmentsByTag(e.CommentRemoved);

        //Draw the newly added comment (this will appear immediately: the view does not need to do a layout). 
        if (e.CommentAdded != null)
            this.DrawComment(e.CommentAdded);
    }
    ```

8. Dodaj procedurę obsługi <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed>.

    ```csharp
    private void OnClosed(object sender, EventArgs e)
    {
        this.provider.Detach();
        this.view.LayoutChanged -= OnLayoutChanged;
        this.view.Closed -= OnClosed;
    }
    ```

9. Dodaj procedurę obsługi <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>.

    ```csharp
    private void OnLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)
    {
        //Get all of the comments that intersect any of the new or reformatted lines of text.
        List<CommentAdornment> newComments = new List<CommentAdornment>();

        //The event args contain a list of modified lines and a NormalizedSpanCollection of the spans of the modified lines.  
        //Use the latter to find the comments that intersect the new or reformatted lines of text. 
        foreach (Span span in e.NewOrReformattedSpans)
        {
            newComments.AddRange(this.provider.GetComments(new SnapshotSpan(this.view.TextSnapshot, span)));
        }

        //It is possible to get duplicates in this list if a comment spanned 3 lines, and the first and last lines were modified but the middle line was not. 
        //Sort the list and skip duplicates.
        newComments.Sort(delegate(CommentAdornment a, CommentAdornment b) { return a.GetHashCode().CompareTo(b.GetHashCode()); });

        CommentAdornment lastComment = null;
        foreach (CommentAdornment comment in newComments)
        {
            if (comment != lastComment)
            {
                lastComment = comment;
                this.DrawComment(comment);
            }
        }
    }
    ```

10. Dodaj prywatną metodę, która rysuje komentarz.

     [!code-csharp[VSSDKMenuCommandTest#35](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_3.cs)]
     [!code-vb[VSSDKMenuCommandTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_3.vb)]

## <a name="use-the-menu-command-to-add-the-comment-adornment"></a>Użyj polecenia menu, aby dodać oznaczenie definiowania komentarza
 Za pomocą polecenia menu można utworzyć znakowanie komentarza, implementując metodę `MenuItemCallback` pakietu VSPackage.

1. Dodaj następujące odwołania do projektu MenuCommandTest:

    - Microsoft. VisualStudio. TextManager. Interop

    - Microsoft. VisualStudio. Editor

    - Microsoft. VisualStudio. Text. UI. WPF

2. Otwórz plik *AddAdornment.cs* i Dodaj następujące dyrektywy `using`.

    ```csharp
    using Microsoft.VisualStudio.TextManager.Interop;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Editor;
    using CommentAdornmentTest;
    ```

3. Usuń metodę `Execute()` i Dodaj następującą procedurę obsługi poleceń.

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
    }
    ```

4. Dodaj kod, aby uzyskać aktywny widok. Aby uzyskać aktywne `IVsTextView`, musisz uzyskać `SVsTextManager` powłoki programu Visual Studio.

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
        IVsTextManager txtMgr = (IVsTextManager) await ServiceProvider.GetServiceAsync(typeof(SVsTextManager));
        IVsTextView vTextView = null;
        int mustHaveFocus = 1;
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);
    }
    ```

5. Jeśli ten widok tekstu jest wystąpieniem widoku tekstu edytora, można go rzutować do interfejsu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>, a następnie uzyskać <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> i powiązane z nim <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>. Użyj <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>, aby wywołać metodę `Connector.Execute()`, która pobiera dostawcę autouzupełniania komentarzy i dodaje moduł definiowania układu. Program obsługi poleceń powinien teraz wyglądać podobnie do tego kodu:

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
        IVsTextManager txtMgr = (IVsTextManager) await ServiceProvider.GetServiceAsync(typeof(SVsTextManager));
        IVsTextView vTextView = null;
        int mustHaveFocus = 1;
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);
        IVsUserData userData = vTextView as IVsUserData;
         if (userData == null)
        {
            Console.WriteLine("No text view is currently open");
            return;
        }
        IWpfTextViewHost viewHost;
        object holder;
        Guid guidViewHost = DefGuidList.guidIWpfTextViewHost;
        userData.GetData(ref guidViewHost, out holder);
        viewHost = (IWpfTextViewHost)holder;
        Connector.Execute(viewHost);
    }
    ```

6. Ustaw metodę AddAdornmentHandler jako procedurę obsługi dla polecenia wypełniania w konstruktorze pre.

    ```csharp
    private AddAdornment(AsyncPackage package, OleMenuCommandService commandService)
    {
        this.package = package ?? throw new ArgumentNullException(nameof(package));
        commandService = commandService ?? throw new ArgumentNullException(nameof(commandService));

        var menuCommandID = new CommandID(CommandSet, CommandId);
        var menuItem = new MenuCommand(this.AddAdornmentHandler, menuCommandID);
        commandService.AddCommand(menuItem);
    }
    ```

## <a name="build-and-test-the-code"></a>Kompiluj i Testuj kod

1. Skompiluj rozwiązanie i Rozpocznij debugowanie. Powinno zostać wyświetlone wystąpienie eksperymentalne.

2. Utwórz plik tekstowy. Wpisz jakiś tekst, a następnie wybierz go.

3. W menu **Narzędzia** kliknij polecenie **Wywołaj Dodawanie definiowania**układu. Dymek powinien być wyświetlany po prawej stronie okna tekstowego i powinien zawierać tekst podobny do poniższego.

     YourUserName

     Fourscore...

## <a name="see-also"></a>Zobacz także
- [Przewodnik: łączenie typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
