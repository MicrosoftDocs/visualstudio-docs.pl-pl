---
title: 'Przewodnik: Używanie polecenia powłoki z rozszerzeniem edytora | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - add a menu command
ms.assetid: 08526848-a442-4cd4-afa1-b2eac2005adb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52b151b09c1bb7306b4270f9408d0f04a7600aa2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697167"
---
# <a name="walkthrough-use-a-shell-command-with-an-editor-extension"></a>Instruktaż: używanie polecenia powłoki z rozszerzeniem edytora
Z VSPackage, można dodać funkcje, takie jak polecenia menu do edytora. W tym przewodniku pokazano, jak dodać ozdoby do widoku tekstu w edytorze, wywołując polecenie menu.

 W tym instruktażu pokazano użycie VSPackage wraz z managed extensibility framework (MEF) składnika. Należy użyć VSPackage zarejestrować polecenie menu z powłoki programu Visual Studio. Można też użyć polecenia, aby uzyskać dostęp do części komponentu MEF.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować visual studio SDK z centrum pobierania. Jest on dołączony jako opcjonalna funkcja w konfiguracji programu Visual Studio. Można również zainstalować vs SDK później. Aby uzyskać więcej informacji, zobacz [Instalowanie pakietu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-menu-command"></a>Tworzenie rozszerzenia za pomocą polecenia menu
 Utwórz pakiet VSPackage, który umieszcza polecenie menu o nazwie **Dodaj ozdobę** w menu **Narzędzia.**

1. Utwórz projekt VSIX `MenuCommandTest`w języku C o nazwie i dodaj nazwę szablonu elementu polecenia niestandardowego **AddAdornment**. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Zostanie otwarte rozwiązanie o nazwie MenuCommandTest. Plik MenuCommandTestPackage ma kod, który tworzy polecenie menu i umieszcza go w menu **Narzędzia.** W tym momencie polecenie po prostu powoduje, że pojawi się okno komunikatu. W dalszej części kroków pokazano, jak to zmienić, aby wyświetlić ozdobę komentarza.

3. Otwórz plik *source.extension.vsixmanifest* w Edytorze manifestów VSIX. Karta `Assets` powinna mieć wiersz dla microsoft.VisualStudio.VsPackage o nazwie MenuCommandTest.

4. Zapisz i zamknij plik *source.extension.vsixmanifest.*

## <a name="add-a-mef-extension-to-the-command-extension"></a>Dodawanie rozszerzenia MEF do rozszerzenia polecenia

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł rozwiązania, kliknij polecenie **Dodaj**, a następnie kliknij polecenie **Nowy projekt**. W oknie dialogowym **Dodawanie nowego projektu** kliknij pozycję **Rozszerzalność** w obszarze **Visual C#**, a następnie **VSIX Project**. Nazwij `CommentAdornmentTest`projekt .

2. Ponieważ ten projekt będzie współdziałać z zestawu VSPackage o silnej nazwie, należy podpisać zestaw. Można ponownie użyć pliku klucza już utworzonego dla zestawu VSPackage.

    1. Otwórz właściwości projektu i wybierz kartę **Podpisywanie.**

    2. Wybierz **pozycję Podpisz złożenie**.

    3. W obszarze **Wybierz plik klucza silnej nazwy**wybierz plik *Key.snk,* który został wygenerowany dla zestawu MenuCommandTest.

## <a name="refer-to-the-mef-extension-in-the-vspackage-project"></a>Zapoznaj się z rozszerzeniem MEF w projekcie VSPackage
 Ponieważ dodajesz składnik MEF do VSPackage, należy określić oba rodzaje zasobów w manifeście.

> [!NOTE]
> Aby uzyskać więcej informacji na temat MEF, zobacz [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-refer-to-the-mef-component-in-the-vspackage-project"></a>Aby odwołać się do składnika MEF w projekcie VSPackage

1. W projekcie MenuCommandTest otwórz plik *source.extension.vsixmanifest* w edytorze manifestów VSIX.

2. Na karcie **Zasoby** kliknij pozycję **Nowy**.

3. Na liście **Typ** wybierz pozycję **Microsoft.VisualStudio.MefComponent**.

4. Na liście **Źródło** wybierz pozycję **Projekt w bieżącym rozwiązaniu**.

5. Na liście **Projekt** wybierz pozycję **CommentAdornmentTest**.

6. Zapisz i zamknij plik *source.extension.vsixmanifest.*

7. Upewnij się, że Projekt MenuCommandTest ma odwołanie do CommentAdornmentTest projektu.

8. W CommentAdornmentTest projektu, ustaw projekt do produkcji zestawu. W **Eksploratorze rozwiązań**wybierz projekt i poszukaj w oknie **Właściwości** właściwości **Kopiuj dane wyjściowe do outputdirectory** i ustaw ją na **true**.

## <a name="define-a-comment-adornment"></a>Definiowanie ozdabiania komentarza
 Sam ozdoba komentarza składa się <xref:Microsoft.VisualStudio.Text.ITrackingSpan> z, który śledzi zaznaczony tekst i niektórych ciągów, które reprezentują autora i opis tekstu.

#### <a name="to-define-a-comment-adornment"></a>Aby zdefiniować ozdobę komentarza

1. W projekcie CommentAdornmentTest dodaj nowy plik klasy `CommentAdornment`i nazwij go .

2. Dodaj następujące odwołania:

    1. Microsoft.VisualStudio.CoreUtility

    2. Microsoft.VisualStudio.Text.Data

    3. Microsoft.VisualStudio.Text.Logic

    4. Microsoft.VisualStudio.Text.UI

    5. Microsoft.VisualStudio.Text.UI.Wpf

    6. System.componentmodel.composition

    7. PrezentacjaCore

    8. PresentationFramework (Ramwork prezentacji)

    9. Windowsbase

3. Dodaj następującą `using` dyrektywę.

    ```csharp
    using Microsoft.VisualStudio.Text;
    ```

4. Plik powinien zawierać klasę `CommentAdornment`o nazwie .

    ```csharp
    internal class CommentAdornment
    ```

5. Dodaj trzy pola `CommentAdornment` do <xref:Microsoft.VisualStudio.Text.ITrackingSpan>klasy dla , autora i opisu.

    ```csharp
    public readonly ITrackingSpan Span;
    public readonly string Author;
    public readonly string Text;
    ```

6. Dodaj konstruktora, który inicjuje pola.

    ```csharp
    public CommentAdornment(SnapshotSpan span, string author, string text)
    {
        this.Span = span.Snapshot.CreateTrackingSpan(span, SpanTrackingMode.EdgeExclusive);
        this.Author = author;
        this.Text = text;
    }
    ```

## <a name="create-a-visual-element-for-the-adornment"></a>Tworzenie elementu wizualnego dla ozdabiania
 Zdefiniuj element wizualny dla ozdabiania. W tym instruktażu należy zdefiniować formant, który dziedziczy <xref:System.Windows.Controls.Canvas>z klasy Windows Presentation Foundation (WPF).

1. Utwórz klasę w projekcie CommentAdornmentTest `CommentBlock`i nazwij ją .

2. Dodaj następujące `using` dyrektywy.

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

3. Spraw, `CommentBlock` aby <xref:System.Windows.Controls.Canvas>klasa dziedziczyła po .

    ```csharp
    internal class CommentBlock : Canvas
    { }
    ```

4. Dodaj kilka pól prywatnych, aby zdefiniować wizualne aspekty ozdabiania.

    ```csharp
    private Geometry textGeometry;
    private Grid commentGrid;
    private static Brush brush;
    private static Pen solidPen;
    private static Pen dashPen;
    ```

5. Dodaj konstruktora, który definiuje ozdoby komentarza i dodaje odpowiedni tekst.

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

6. Zaimplementuj <xref:System.Windows.Controls.Panel.OnRender%2A> również program obsługi zdarzeń, który rysuje ozdoby.

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

## <a name="add-an-iwpftextviewcreationlistener"></a>Dodawanie listy iWpfTextViewCreationListener
 Jest <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> częścią składnika MEF, której można użyć do nasłuchiwać zdarzeń tworzenia.

1. Dodaj plik klasy do projektu CommentAdornmentTest `Connector`i nazwij go .

2. Dodaj następujące `using` dyrektywy.

    ```csharp
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Utilities;
    ```

3. Deklaruj <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>klasę, która implementuje , i <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> eksportuj ją z "tekstem" i a . <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> Atrybut typu zawartości określa rodzaj zawartości, do której ma zastosowanie składnik. Typ tekstu jest typem podstawowym dla wszystkich niebinarnych typów plików. W związku z tym prawie każdy widok tekstu, który jest tworzony będzie tego typu. Atrybut roli widoku tekstu określa rodzaj widoku tekstu, do którego stosuje się składnik. Role widoku tekstu dokumentu zazwyczaj pokazują tekst, który składa się z wierszy i jest przechowywany w pliku.

     [!code-vb[VSSDKMenuCommandTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_1.vb)]
     [!code-csharp[VSSDKMenuCommandTest#11](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_1.cs)]

4. Zaimplementuj <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> metodę tak, aby wywołuje zdarzenie statyczne `Create()` `CommentAdornmentManager`.

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

## <a name="define-an-adornment-layer"></a>Definiowanie warstwy ozdabiania
 Aby dodać nowe ozdoby, należy zdefiniować warstwę ozdabiania.

### <a name="to-define-an-adornment-layer"></a>Aby zdefiniować warstwę ozdabianie

1. W `Connector` klasie zadeklarować pole publiczne <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>typu i wyeksportować go <xref:Microsoft.VisualStudio.Utilities.NameAttribute> z, który określa unikatową nazwę dla warstwy ozdabiania i który definiuje relację <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> z kolejnością tej warstwy ozdabiania do innych warstw widoku tekstu (tekst, karetka i zaznaczenie).

    ```csharp
    [Export(typeof(AdornmentLayerDefinition))]
    [Name("CommentAdornmentLayer")]
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
    public AdornmentLayerDefinition commentLayerDefinition;

    ```

## <a name="provide-comment-adornments"></a>Podaj ozdoby komentarzy
 Podczas definiowania ozdabiania, należy również zaimplementować dostawcy ozdabień komentarza i menedżera ozdabiania komentarza. Dostawca ozdób komentarzy przechowuje listę ozdób komentarzy, <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> nasłuchuje zdarzeń w buforze tekstu źródłowego i usuwa ozdoby komentarza po usunięciu tekstu źródłowego.

1. Dodaj nowy plik klasy do projektu CommentAdornmentTest i nazwij go `CommentAdornmentProvider`.

2. Dodaj następujące `using` dyrektywy.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Collections.ObjectModel;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Editor;
    ```

3. Dodaj klasę `CommentAdornmentProvider`o nazwie .

    ```csharp
    internal class CommentAdornmentProvider
    {
    }
    ```

4. Dodaj pola prywatne dla buforu tekstowego i listę ozdób komentarzy związanych z buforem.

    ```csharp
    private ITextBuffer buffer;
    private IList<CommentAdornment> comments = new List<CommentAdornment>();

    ```

5. Dodaj konstruktora dla `CommentAdornmentProvider`. Ten konstruktor powinien mieć dostęp prywatny, ponieważ `Create()` dostawca jest tworzone przez metodę. Konstruktor dodaje `OnBufferChanged` program obsługi <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> zdarzeń do zdarzenia.

    ```csharp
    private CommentAdornmentProvider(ITextBuffer buffer)
    {
        this.buffer = buffer;
        //listen to the Changed event so we can react to deletions. 
        this.buffer.Changed += OnBufferChanged;
    }

    ```

6. Dodaj `Create()` metodę.

    ```csharp
    public static CommentAdornmentProvider Create(IWpfTextView view)
    {
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentProvider>(delegate { return new CommentAdornmentProvider(view.TextBuffer); });
    }

    ```

7. Dodaj `Detach()` metodę.

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

8. Dodaj `OnBufferChanged` program obsługi zdarzeń.

     [!code-csharp[VSSDKMenuCommandTest#21](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_2.cs)]
     [!code-vb[VSSDKMenuCommandTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_2.vb)]

9. Dodaj deklarację `CommentsChanged` dla zdarzenia.

    ```csharp
    public event EventHandler<CommentsChangedEventArgs> CommentsChanged;
    ```

10. Utwórz `Add()` metodę, aby dodać ozdoby.

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

11. Dodaj `RemoveComments()` metodę.

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

12. Dodaj `GetComments()` metodę, która zwraca wszystkie komentarze w danym zakresie migawki.

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

13. Dodaj klasę `CommentsChangedEventArgs`o nazwie , w następujący sposób.

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

## <a name="manage-comment-adornments"></a>Zarządzanie ozdobami komentarzy
 Menedżer ozdabiania komentarza tworzy ozdoby i dodaje go do warstwy ozdabiania. Nasłuchuje <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> i <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> zdarzeń, dzięki czemu można przenieść lub usunąć ozdoby. Nasłuchuje również `CommentsChanged` zdarzenia, które jest uruchamiane przez dostawcę ozdabiania komentarzy, gdy komentarze są dodawane lub usuwane.

1. Dodaj plik klasy do projektu CommentAdornmentTest `CommentAdornmentManager`i nazwij go .

2. Dodaj następujące `using` dyrektywy.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Windows.Media;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Text.Formatting;
    ```

3. Dodaj klasę `CommentAdornmentManager`o nazwie .

    ```csharp
    internal class CommentAdornmentManager
        {
        }
    ```

4. Dodaj kilka pól prywatnych.

    ```csharp
    private readonly IWpfTextView view;
    private readonly IAdornmentLayer layer;
    private readonly CommentAdornmentProvider provider;
    ```

5. Dodaj konstruktora, który subskrybuje menedżera do <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> i <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> zdarzeń, a także do `CommentsChanged` zdarzenia. Konstruktor jest prywatny, ponieważ menedżer jest tworzone `Create()` przez metodę statyczną.

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

6. Dodaj `Create()` metodę, która pobiera dostawcę lub tworzy go w razie potrzeby.

    ```csharp
    public static CommentAdornmentManager Create(IWpfTextView view)
    {
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentManager>(delegate { return new CommentAdornmentManager(view); });
    }
    ```

7. Dodaj `CommentsChanged` program obsługi.

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

8. Dodaj <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> program obsługi.

    ```csharp
    private void OnClosed(object sender, EventArgs e)
    {
        this.provider.Detach();
        this.view.LayoutChanged -= OnLayoutChanged;
        this.view.Closed -= OnClosed;
    }
    ```

9. Dodaj <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> program obsługi.

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

10. Dodaj metodę prywatną, która rysuje komentarz.

     [!code-csharp[VSSDKMenuCommandTest#35](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_3.cs)]
     [!code-vb[VSSDKMenuCommandTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_3.vb)]

## <a name="use-the-menu-command-to-add-the-comment-adornment"></a>Użyj polecenia menu, aby dodać ozdobę komentarza
 Za pomocą polecenia menu można utworzyć ozdobę komentarza, `MenuItemCallback` implementując metodę VSPackage.

1. Dodaj następujące odwołania do projektu MenuCommandTest:

    - Microsoft.VisualStudio.TextManager.Interop

    - Edytor Microsoft.VisualStudio.Editor

    - Microsoft.VisualStudio.Text.UI.Wpf

2. Otwórz plik *AddAdornment.cs* i dodaj następujące `using` dyrektywy.

    ```csharp
    using Microsoft.VisualStudio.TextManager.Interop;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Editor;
    using CommentAdornmentTest;
    ```

3. Usuń `Execute()` metodę i dodaj następujący program obsługi poleceń.

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
    }
    ```

4. Dodaj kod, aby uzyskać aktywny widok. Aby uzyskać `SVsTextManager` aktywną powłokę programu Visual `IVsTextView`Studio, należy uzyskać powłokę programu Visual Studio.

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
        IVsTextManager txtMgr = (IVsTextManager) await ServiceProvider.GetServiceAsync(typeof(SVsTextManager));
        IVsTextView vTextView = null;
        int mustHaveFocus = 1;
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);
    }
    ```

5. Jeśli ten widok tekstu jest wystąpieniem widoku tekstu edytora, można go przerzucić do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> interfejsu, a następnie uzyskać <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> skojarzone <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>z nim . Użyj <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> wywołać `Connector.Execute()` metodę, która pobiera dostawcy ozdabiania komentarza i dodaje ozdoby. Program obsługi poleceń powinien teraz wyglądać następująco:

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

6. Ustaw AddAdornmentHandler metoda jako program obsługi addAdornment polecenia w AddAdornment konstruktora.

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

## <a name="build-and-test-the-code"></a>Tworzenie i testowanie kodu

1. Skompiluj rozwiązanie i rozpocznij debugowanie. Powinno pojawić się wystąpienie eksperymentalne.

2. Tworzenie pliku tekstowego. Wpisz tekst, a następnie zaznacz go.

3. W menu **Narzędzia** kliknij polecenie **Wywołaj dodaj ozdobę**. Dymek powinien być wyświetlany po prawej stronie okna tekstu i powinien zawierać tekst przypominający następujący tekst.

     TwojaName użytkownika

     Fourscore...

## <a name="see-also"></a>Zobacz też
- [Instruktaż: łączenie typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
